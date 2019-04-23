---
title: Создание пространства имен DFS
description: В этой статье рассматривается, как создать пространство имен DFS.
ms.date: 6/5/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 4256e124e75be72f94cbd35c182edfe38e92bc90
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59847505"
---
# <a name="create-a-dfs-namespace"></a>Создание пространства имен DFS

> Относится к: Windows Server 2019, Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Чтобы создать новое пространство имен, можно использовать диспетчер сервера для создания пространства имен при установке службы роли "Пространства имен DFS". Также можно использовать [командлет New-DfsnRoot](https://docs.microsoft.com/powershell/module/dfsn/new-dfsnroot) из сеанса Windows PowerShell. 

Модуль DFSN Windows PowerShell был введен в Windows Server 2012. 

Другой вариант — использовать следующую процедуру для создания пространства имен после установки службы роли.

## <a name="to-create-a-namespace"></a>Создание пространства имен

1.  Нажмите кнопку **Пуск**, наведите курсор на **Администрирование** и щелкните **Управление DFS**.

2.  В дереве консоли щелкните правой кнопкой мыши узел **Пространства имен** и выберите **Новое пространство имен**.

3.  Следуйте инструкциям в **Мастере создания нового пространства имен**.

    Чтобы создать изолированное пространство имен в отказоустойчивом кластере, укажите имя экземпляра кластерного файлового сервера на странице **Сервер пространства имен** в **Мастере создания нового пространства имен**.

> [!IMPORTANT]
> Не пытайтесь создать доменное пространство имен, с помощью режима Windows Server 2008, если режим работы леса Windows Server 2003 или более поздней версии. В противном случае в пространстве имен, для которого нельзя удалить папки DFS, выдавая сообщение об ошибке: «Невозможно удалить папку. Не удается завершить выполнение функции".

## <a name="see-also"></a>См. также

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Выбор типа пространства имен](choose-a-namespace-type.md)
-   [Добавить серверы пространств имен для пространства имен DFS на основе домена](add-namespace-servers-to-a-domain-based-dfs-namespace.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md).


