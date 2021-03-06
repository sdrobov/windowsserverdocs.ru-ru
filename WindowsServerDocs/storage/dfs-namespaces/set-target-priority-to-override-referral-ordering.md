---
title: Задание приоритета конечных объектов для переопределения порядка в ссылках
description: В этой статье рассматривается, как задать приоритет конечных объектов для переопределения порядка в ссылках.
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 77fe5b82b73a0f37ba81dda210f15d6017788822
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966826"
---
# <a name="set-target-priority-to-override-referral-ordering"></a>Задание приоритета конечных объектов для переопределения порядка в ссылках

> Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Ссылка — это упорядоченный список конечных объектов, которые клиентский компьютер получает от контроллера домена или сервера пространства имен, когда пользователь обращается к корню пространства имен или папке с конечными объектами в пространстве имен. Каждый конечный объект в ссылке упорядочен согласно методу сортировки для корня или папки пространства имен.

Порядок конечных объектов можно уточнить, установив приоритет отдельных конечных объектов. Например, можно указать, что конечный объект должен быть первым (или последним) из всех конечных объектов либо первым (или последним) из всех конечных объектов с равной стоимостью подключения.

## <a name="to-set-target-priority-on-a-root-target-for-a-domain-based-namespace"></a>Установка приоритета корневого конечного объекта для доменного пространства имен

Чтобы задать приоритет корневого конечного объекта для доменного пространства имен, выполните следующие действия:

1.  Нажмите кнопку **Пуск**, укажите пункт **Администрирование**, а затем щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните доменное пространство имен для корневых конечных объектов, для которых вы хотите задать приоритет.

3.  В области **Сведения** на вкладке **Серверы пространства имен** щелкните правой кнопкой мыши корневой конечный объект с приоритетом, который необходимо изменить, и выберите **Свойства**.

4.  На вкладке **Дополнительно** щелкните **Переопределить сортировку ссылок**, а затем выберите требуемый приоритет.

    -   **Первый из всех конечных объектов** — указывает, что пользователи всегда будут направляться на этот конечный объект, если он доступен.
    -   **Последний из всех конечных объектов** — указывает, что пользователи будут направляться на этот конечный объект только тогда, когда все другие конечные объекты недоступны.
    -   **Первый из конечных объектов равной цены** — указывает, что пользователи будут направляться на этот конечный объект до других конечных объектов с равной стоимостью подключения (которыми обычно являются другие конечные объекты на том же сайте).
    -   **Последний из конечных объектов равной цены** — указывает, что пользователи не будут направляться на этот конечный объект, если доступны другие конечные объекты с равной стоимостью подключения (которыми обычно являются другие конечные объекты на том же сайте).

## <a name="to-set-target-priority-on-a-folder-target"></a>Установка приоритета для конечного объекта папки

Чтобы задать приоритет конечного объекта папки, выполните следующие действия:

1.  Нажмите кнопку **Пуск**, укажите пункт **Администрирование**, а затем щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните папку для конечных объектов, для которых вы хотите установить приоритет.

3.  В области **Свойства** на вкладке **Конечные объекты папки** щелкните правой кнопкой мыши конечный объект папки с приоритетом, который необходимо изменить, и выберите **Свойства**.

4.  На вкладке **Дополнительно** щелкните **Переопределить сортировку ссылок**, а затем выберите требуемый приоритет.

> [!NOTE]
> Чтобы задать приоритеты конечных объектов с помощью Windows PowerShell, используйте командлеты [Set-DfsnRootTarget](/powershell/module/dfsr/update-dfsrconfigurationfromad?view=win10-ps) и [Set-DfsnFolderTarget](/powershell/module/dfsr/update-dfsrconfigurationfromad?view=win10-ps) с параметрами **ReferralPriorityClass** и **ReferralPriorityRank**. Эти командлеты были введены в Windows Server 2012.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Настройка пространств имен DFS](tuning-dfs-namespaces.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md)
