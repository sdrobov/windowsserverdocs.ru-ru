---
title: Добавление конечных объектов папок
description: В этом разделе рассматривается, как добавлять конечные объекты папок (UNC-пути)
ms.prod: windows-server
ms.author: jgerend
manager: brianlic
ms.technology: storage
ms.topic: article
author: jasongerend
ms-date: 06/05/2017
ms.openlocfilehash: e5a81f2967953b985028407d53d6a039fd8990eb
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86961276"
---
# <a name="add-folder-targets"></a>Добавление конечных объектов папок

> Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Конечный объект папки — это путь в формате UNC к общей папке или к другому пространству имен, которое связано с папкой в пространстве имен. Добавление нескольких конечных объектов папки повышает доступность папки в пространстве имен.

## <a name="to-add-a-folder-target"></a>Добавление конечного объекта папки

Чтобы добавить конечный объект папки с помощью оснастки "Управление DFS", выполните следующие действия:

1.  Нажмите кнопку **Пуск**, укажите пункт **Администрирование**, а затем щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните правой кнопкой мыши папку и выберите **Добавить конечный объект папки**.

3.  Введите путь к конечному объекту папки или нажмите кнопку **Обзор**, чтобы найти конечный объект папки.

4.  Если папка реплицируется с помощью репликации DFS, можно указать, следует ли добавить новый конечный объект папки в группу репликации.

> [!TIP]
> Чтобы добавить конечный объект папки с помощью Windows PowerShell, используйте командлет [New-DfsnFolderTarget](/powershell/module/dfsn/new-dfsnfoldertarget). Модуль DFSN Windows PowerShell был введен в Windows Server 2012.

> [!NOTE]
> Папки могут содержать конечные объекты папок или другие папки DFS, но не и те и другие на одном и том же уровне в иерархии папок.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md)
-   [Репликация целевых объектов папки с помощью репликация DFS](replicate-folder-targets-using-dfs-replication.md)
