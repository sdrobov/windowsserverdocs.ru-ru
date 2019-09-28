---
title: Добавление конечных объектов папок
description: В этом разделе рассматривается, как добавлять конечные объекты папок (UNC-пути)
ms.prod: windows-server
ms.author: jgerend
ms.manager: brianlic
ms.technology: storage
ms.topic: article
author: jasongerend
ms-date: 06/05/2017
ms.openlocfilehash: b0685ea795d53b36fad92d54f817f67de57e3a82
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403190"
---
# <a name="add-folder-targets"></a>Добавление конечных объектов папок

> Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Конечный объект папки — это путь в формате UNC к общей папке или к другому пространству имен, которое связано с папкой в пространстве имен. Добавление нескольких конечных объектов папки повышает доступность папки в пространстве имен.

## <a name="to-add-a-folder-target"></a>Добавление конечного объекта папки

Чтобы добавить конечный объект папки с помощью оснастки "Управление DFS", выполните следующие действия:

1.  Нажмите кнопку **Пуск**, наведите курсор на **Администрирование** и щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните правой кнопкой мыши папку и выберите **Добавить конечный объект папки**.

3.  Введите путь к конечному объекту папки или нажмите кнопку **Обзор**, чтобы найти конечный объект папки.

4.  Если папка реплицируется с помощью репликации DFS, можно указать, следует ли добавить новый конечный объект папки в группу репликации.

> [!TIP]
> Чтобы добавить конечный объект папки с помощью Windows PowerShell, используйте командлет [New-DfsnFolderTarget](https://docs.microsoft.com/powershell/module/dfsn/new-dfsnfoldertarget). Модуль DFSN Windows PowerShell был введен в Windows Server 2012.

> [!NOTE]
> Папки могут содержать конечные объекты папок или другие папки DFS, но не и те и другие на одном и том же уровне в иерархии папок.

## <a name="see-also"></a>См. также

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md)
-   [Репликация целевых объектов папки с помощью репликация DFS](replicate-folder-targets-using-dfs-replication.md)