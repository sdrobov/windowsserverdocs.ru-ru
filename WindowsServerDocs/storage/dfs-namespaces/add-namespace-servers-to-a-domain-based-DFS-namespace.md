---
title: "Добавление серверов пространства имен в доменное пространство имен DFS"
description: "В этой статье рассматривается, как указать дополнительные сервера пространства имен для размещения пространства имен с помощью оснастки \"Управление DFS\"."
ms.date: 6/5/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 70ab3cac71f5766bc572015c6b23c0937e5252f0
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="add-namespace-servers-to-a-domain-based-dfs-namespace"></a>Добавление серверов пространств имен в доменное пространство имен DFS

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Доступность доменного пространства имен можно повысить, указав дополнительные сервера пространства имен для размещения пространства имен.

## <a name="to-add-a-namespace-server-to-a-domain-based-namespace"></a>Добавление сервера пространства имен в доменное пространство имен

Чтобы добавить сервер пространства имен в доменное пространство имен с помощью оснастки "Управление DFS", выполните следующие действия:

1.  Нажмите кнопку **Пуск**, наведите курсор на **Администрирование** и щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните правой кнопкой мыши доменное пространство имен и выберите **Добавить сервер пространства имен**.

3.  Введите путь к другому серверу или нажмите кнопку **Обзор**, чтобы найти сервер.

> [!NOTE]
> Эта процедура не применяется для изолированных пространств имен, поскольку они поддерживают только один сервер пространства имен. Чтобы повысить доступность изолированного пространства имен, укажите в качестве сервера пространства имен в мастере создания пространства имен отказоустойчивый кластер.


> [!TIP]
> Чтобы добавить сервер пространства имен с помощью Windows PowerShell, используйте командлет [New-DfsnRootTarget](https://docs.microsoft.com/powershell/module/dfsn/set-dfsnroottarget). Модуль DFSN Windows PowerShell был введен в Windows Server 2012.

## <a name="see-also"></a>См. также

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Обзор требований к серверу пространств имен DFS](https://technet.microsoft.com/library/cc753448(v=ws.11).aspx)
-   [Создание пространства имен DFS](create-a-dfs-namespace.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md)

