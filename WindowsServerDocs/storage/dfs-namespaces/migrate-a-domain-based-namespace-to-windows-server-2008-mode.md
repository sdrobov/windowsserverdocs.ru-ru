---
title: Перенос доменного пространства имен в режим Windows Server 2008
description: В этой статье описано, как перенести доменное пространство имен в режим Windows Server 2008.
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 3aa7743773a8a6e9ed22c0f626c2c6a0dbafce56
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85475471"
---
# <a name="migrate-a-domain-based-namespace-to-windows-server-2008-mode"></a>Перенос доменного пространства имен в режим Windows Server 2008

> Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Режим Windows Server 2008 для доменных пространств имен предусматривает поддержку перечисления на основе доступа и повышенную масштабируемость.

## <a name="to-migrate-a-domain-based-namespace-to-windows-server-2008-mode"></a>Перенос доменного пространства имен в режим Windows Server 2008

Для переноса доменного пространства имен из режима Windows 2000 Server в режим Windows Server 2008 необходимо экспортировать пространство имен в файл, удалить пространство имен, заново создать его в режиме Windows Server 2008, а затем импортировать параметры пространства имен. Чтобы это сделать, выполните следующие действия:

1.  Откройте окно командной строки и введите следующую команду, чтобы экспортировать пространство имен в файл, где \\ \\ *доменное* \\ *пространство имен* — это имя соответствующего домена, а пространство имен и *путь к \\ * файлу — это путь и имя файла для экспорта:
     ```
     Dfsutil root export \\domain\namespace path\filename.xml
     ```
2.  Запишите путь ( \\ \\ *server* \\ *Общая папка* сервера) для каждого сервера пространства имен. Необходимо вручную добавить серверы пространства имен во вновь созданное пространство имен, поскольку команда Dfsutil не может импортировать серверы пространства имен.
3.  В оснастке "Управление DFS" щелкните правой кнопкой мыши пространство имен и выберите **Удалить**, или введите в командной строке следующую команду, <br /> где \\ \\ *доменное* \\ *пространство имен* — это имя соответствующего домена и пространства имен:
     ```
     Dfsutil root remove \\domain\namespace
     ```
4.  В оснастке "Управление DFS" заново создайте пространство имен с тем же именем, но с использованием режима Windows Server 2008, или введите в командной строке следующую команду, где <br /> \\\\*Серверная* \\ *пространство имен* — это имя соответствующего сервера и общего ресурса для корня пространства имен:
     ```
     Dfsutil root adddom \\server\namespace v2
     ```
5.  Чтобы импортировать пространство имен из файла экспорта, введите в командной строке следующую команду, где <br /> \\\\*домен* \\ *пространство имен* — это имя соответствующего домена и пространства имен, а имя файла *пути \\ * — это путь к импортируемому файлу в файле:
     ```
     Dfsutil root import merge path\filename.xml \\domain\namespace
     ```

    > [!NOTE]
    > Чтобы свести к минимуму время, необходимое для импорта большого пространства имен, выполняете команду импорта корня **Dfsutil** локально на сервере пространства имен.
6.  Добавьте все остальные серверы пространства имен во вновь созданное пространство имен, щелкнув правой кнопкой мыши пространство имен в оснастке "Управление DFS" и выбрав команду **Добавить сервер пространства имен**, или, введя в командной строке следующую команду, где <br /> \\\\*Серверная* \\ *Share* — это имя соответствующего сервера и общего ресурса для корня пространства имен:
     ```
     Dfsutil target add \\server\share
     ```

    > [!NOTE]
    > Можно добавить серверы пространства имен перед импортом пространства имен, однако в этом случае серверы пространства имен будут загружать метаданные для пространства имен инкрементным образом, а не загружать все пространство имен сразу же после добавления в качестве сервера пространства имен.

## <a name="additional-references"></a>Дополнительные ссылки
-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Выбор типа пространства имен](choose-a-namespace-type.md)