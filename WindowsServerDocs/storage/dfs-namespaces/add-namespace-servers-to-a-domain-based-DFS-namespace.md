---
title: Добавление серверов пространства имен в доменное пространство имен DFS
description: В этой статье рассматривается, как указать дополнительные сервера пространства имен для размещения пространства имен с помощью оснастки "Управление DFS".
ms.date: 6/5/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 03b6920e75ba3c51f1d181cfd41887fef39b7412
ms.sourcegitcommit: 0467b8e69de66e3184a42440dd55cccca584ba95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546323"
---
# <a name="add-namespace-servers-to-a-domain-based-dfs-namespace"></a>Добавление серверов пространств имен в доменное пространство имен DFS

> Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Доступность доменного пространства имен можно повысить, указав дополнительные сервера пространства имен для размещения пространства имен.

## <a name="to-add-a-namespace-server-to-a-domain-based-namespace"></a>Добавление сервера пространства имен в доменное пространство имен

Чтобы добавить сервер пространства имен в доменное пространство имен с помощью оснастки "Управление DFS", выполните следующие действия:

1.  Нажмите кнопку **Пуск**, наведите курсор на **Администрирование** и щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните правой кнопкой мыши доменное пространство имен и выберите **Добавить сервер пространства имен**.

3.  Введите путь к другому серверу или нажмите кнопку **Обзор**, чтобы найти сервер.

> [!NOTE]
> Эта процедура не применяется для изолированных пространств имен, поскольку они поддерживают только один сервер пространства имен. Чтобы повысить доступность изолированного пространства имен, укажите в качестве сервера пространства имен в мастере создания пространства имен отказоустойчивый кластер.


> [!TIP]
> Чтобы добавить сервер пространства имен с помощью Windows PowerShell, используйте командлет [New-DfsnRootTarget](https://docs.microsoft.com/powershell/module/dfsn/new-dfsnroottarget). Модуль DFSN Windows PowerShell был введен в Windows Server 2012.

## <a name="see-also"></a>См. также

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Ознакомьтесь с требованиями к серверу пространств имен DFS](https://technet.microsoft.com/library/cc753448(v=ws.11).aspx)
-   [Создание пространства имен DFS](create-a-dfs-namespace.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md)

