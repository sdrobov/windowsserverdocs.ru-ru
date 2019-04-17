---
title: "Создание папки в пространстве имен DFS"
description: "В этой статье рассматривается, как папку в пространстве имен DFS."
ms.date: 6/5/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 1ca9fa0b87c6e995f3f0c38abec80fef9068df90
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="create-a-folder-in-a-dfs-namespace"></a>Создание папки в пространстве имен DFS

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Папки можно использовать для создания дополнительных уровней иерархии в пространстве имен. Можно также создавать папки с конечными объектами папок, чтобы добавлять в пространство имен общие папки. Папки DFS с конечными объектами папок не могут содержать другие папки DFS, поэтому, если вы хотите добавить в пространство имен уровень иерархии, не добавляйте в папку конечные объекты папки.

Выполните следующие действия, чтобы создать папку в пространстве имен с помощью оснастки "Управление DFS":

## <a name="to-create-a-folder-in-a-dfs-namespace"></a>Создание папки в пространстве имен DFS

1.  Нажмите кнопку **Пуск**, наведите курсор на **Администрирование** и щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните правой кнопкой мыши пространство имен или папку внутри пространства имен и выберите **Новая папка**.

3.  В текстовом поле **Имя** введите имя новой папки.

4.  Чтобы добавить в папку один или несколько конечных объектов папки, нажмите кнопку **Добавить** и укажите UNC-путь к конечному объекту папки, а затем нажмите **ОК**.


> [!TIP]
> Чтобы создать папку в пространстве имен с помощью Windows PowerShell, используйте командлет [New-DfsnFolder](https://docs.microsoft.com/powershell/module/dfsn/new-dfsnfolder). Модуль DFSN Windows PowerShell был введен в Windows Server 2012.


## <a name="see-also"></a>См. также

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md)


