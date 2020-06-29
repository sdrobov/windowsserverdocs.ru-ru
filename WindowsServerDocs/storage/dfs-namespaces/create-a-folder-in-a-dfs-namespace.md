---
title: Создание папки в пространстве имен DFS
description: В этой статье рассматривается, как папку в пространстве имен DFS.
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 18e0f1ad19e8c6ce2b6dbffe0d25c940c4f8f985
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474281"
---
# <a name="create-a-folder-in-a-dfs-namespace"></a>Создание папки в пространстве имен DFS

> Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Папки можно использовать для создания дополнительных уровней иерархии в пространстве имен. Можно также создавать папки с конечными объектами папок, чтобы добавлять в пространство имен общие папки. Папки DFS с конечными объектами папок не могут содержать другие папки DFS, поэтому, если вы хотите добавить в пространство имен уровень иерархии, не добавляйте в папку конечные объекты папки.

Выполните следующие действия, чтобы создать папку в пространстве имен с помощью оснастки "Управление DFS":

## <a name="to-create-a-folder-in-a-dfs-namespace"></a>Создание папки в пространстве имен DFS

1.  Нажмите кнопку **Пуск**, укажите пункт **Администрирование**, а затем щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните правой кнопкой мыши пространство имен или папку внутри пространства имен и выберите **Новая папка**.

3.  В текстовом поле **Имя** введите имя новой папки.

4.  Чтобы добавить в папку один или несколько конечных объектов папки, нажмите кнопку **Добавить** и укажите UNC-путь к конечному объекту папки, а затем нажмите **ОК**.


> [!TIP]
> Чтобы создать папку в пространстве имен с помощью Windows PowerShell, используйте командлет [New-DfsnFolder](https://docs.microsoft.com/powershell/module/dfsn/new-dfsnfolder). Модуль DFSN Windows PowerShell был введен в Windows Server 2012.


## <a name="additional-references"></a>Дополнительные ссылки

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md)


