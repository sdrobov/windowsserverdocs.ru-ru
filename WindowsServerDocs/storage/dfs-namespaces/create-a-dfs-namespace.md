---
title: "Создание пространства имен DFS"
description: "В этой статье рассматривается, как создать пространство имен DFS."
ms.date: 6/5/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: b01a83f165e0ef01c6413dcf8785435c8f3aca5a
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="create-a-dfs-namespace"></a>Создание пространства имен DFS

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Чтобы создать новое пространство имен, можно использовать диспетчер сервера для создания пространства имен при установке службы роли "Пространства имен DFS". Также можно использовать [командлет New-DfsnRoot](https://docs.microsoft.com/powershell/module/dfsn/new-dfsnroot) из сеанса Windows PowerShell. 

Модуль DFSN Windows PowerShell был введен в Windows Server 2012. 

Другой вариант — использовать следующую процедуру для создания пространства имен после установки службы роли.

## <a name="to-create-a-namespace"></a>Создание пространства имен

1.  Нажмите кнопку **Пуск**, наведите курсор на **Администрирование** и щелкните **Управление DFS**.

2.  В дереве консоли щелкните правой кнопкой мыши узел **Пространства имен** и выберите **Новое пространство имен**.

3.  Следуйте инструкциям в **Мастере создания нового пространства имен**.

    Чтобы создать изолированное пространство имен в отказоустойчивом кластере, укажите имя экземпляра кластерного файлового сервера на странице **Сервер пространства имен** в **Мастере создания нового пространства имен**.

> [!IMPORTANT]
> Не пытайтесь создавать доменное пространство имен с использованием режима Windows Server 2008, если режим работы леса — Windows Server 2003 или выше. В противном случае вы получите пространство имен, в котором не сможете удалять папки DFS. Будет появляться следующее сообщение об ошибке: "Невозможно удалить папку. Не удается завершить выполнение функции".

## <a name="see-also"></a>См. также

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Выбор типа пространства имен](choose-a-namespace-type.md)
-   [Добавление серверов пространства имен в доменное пространство имен DFS](add-namespace-servers-to-a-domain-based-dfs-namespace.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md).


