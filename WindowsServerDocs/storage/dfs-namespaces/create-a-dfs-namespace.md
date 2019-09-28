---
title: Создание пространства имен DFS
description: В этой статье рассматривается, как создать пространство имен DFS.
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: f4d4b86dd1a105576ac4d1749213696b319ba528
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402210"
---
# <a name="create-a-dfs-namespace"></a>Создание пространства имен DFS

> Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Чтобы создать новое пространство имен, можно использовать диспетчер сервера для создания пространства имен при установке службы роли "Пространства имен DFS". Также можно использовать [командлет New-DfsnRoot](https://docs.microsoft.com/powershell/module/dfsn/new-dfsnroot) из сеанса Windows PowerShell. 

Модуль DFSN Windows PowerShell был введен в Windows Server 2012. 

Другой вариант — использовать следующую процедуру для создания пространства имен после установки службы роли.

## <a name="to-create-a-namespace"></a>Создание пространства имен

1.  Нажмите кнопку **Пуск**, наведите курсор на **Администрирование** и щелкните **Управление DFS**.

2.  В дереве консоли щелкните правой кнопкой мыши узел **Пространства имен** и выберите **Новое пространство имен**.

3.  Следуйте инструкциям в **Мастере создания нового пространства имен**.

    Чтобы создать изолированное пространство имен в отказоустойчивом кластере, укажите имя экземпляра кластерного файлового сервера на странице **Сервер пространства имен** в **Мастере создания нового пространства имен**.

> [!IMPORTANT]
> Не пытайтесь создать пространство имен на основе домена, используя режим Windows Server 2008, если режим работы леса не равен Windows Server 2003 или более поздней версии. Это может привести к созданию пространства имен, для которого нельзя удалить папки DFS, при этом выдается следующее сообщение об ошибке: "Не удается удалить папку. Не удается завершить выполнение функции".

## <a name="see-also"></a>См. также

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Выбор типа пространства имен](choose-a-namespace-type.md)
-   [Добавление серверов пространств имен в доменное пространство имен DFS](add-namespace-servers-to-a-domain-based-dfs-namespace.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md).


