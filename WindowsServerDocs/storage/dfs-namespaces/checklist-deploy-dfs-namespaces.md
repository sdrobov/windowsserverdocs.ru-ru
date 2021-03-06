---
title: Контрольный список развертывания пространств имен DFS
description: В этой статье рассматривается, как настраивать и развертывать пространства имен DFS.
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 389d02ae7269ef48ef77d066db3064759d9253c1
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86961966"
---
# <a name="checklist-deploy-dfs-namespaces"></a>Контрольный список: развертывание пространств имен DFS

> Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Пространства имен распределенной файловой системы (DFS) и репликация DFS могут использоваться для публикации документов, программного обеспечения и бизнес-данных для пользователей в масштабах всей организации. Несмотря на то что одной репликации DFS недостаточно для распространения данных, используя пространства имен DFS, можно настроить пространство имен так, чтобы папка размещалась на нескольких серверах, причем на каждом из них находилась актуальная копия папки. Это повышает доступность данных и позволяет распределять клиентскую нагрузку по серверам.

При просмотре папок в пространстве имен пользователи не знают о том, что папка размещена на нескольких серверах. Когда пользователь открывает папку, клиентский компьютер автоматически перенаправляется на сервер на его сайте. При отсутствии серверов на том же сайте можно настроить пространство так, чтобы клиент перенаправлялся на сервер с наименьшей стоимостью подключения, определенной в службах каталогов Active Directory (AD DS).

Для развертывания пространств имен DFS выполните следующие задачи:

-   Ознакомьтесь с понятиями и требованиями, связанными с пространствами имен DFS.
[Обзор пространств имен DFS](dfs-overview.md)
-   [Выбор типа пространства имен](choose-a-namespace-type.md)
-   [Создание пространства имен DFS](create-a-dfs-namespace.md)
-   Перенесите существующие доменные пространства имен в доменные пространства имен режима Windows Server 2008. [Миграция пространства имен на основе домена в режим Windows Server 2008](migrate-a-domain-based-namespace-to-windows-server-2008-mode.md)
-   Повысьте доступность путем добавления в доменное пространство имен серверов пространства имен. [Добавление серверов пространств имен в доменное пространство имен DFS](add-namespace-servers-to-a-domain-based-dfs-namespace.md)
-   Добавьте в пространство имен папки. [Создание папки в пространстве имен DFS](create-a-folder-in-a-dfs-namespace.md)
-   Добавьте в папки в пространстве имен конечные объекты папок. [Добавление конечных объектов папок](add-folder-targets.md)
-   Реплицируйте содержимое между конечными объектами папок с помощью репликации DFS (необязательно). [Репликация целевых объектов папки с помощью репликация DFS](replicate-folder-targets-using-dfs-replication.md)


## <a name="additional-references"></a>Дополнительные ссылки

-   [Пространства имен](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771914(v=ws.11))
-   [Контрольный список. Настройка пространства имен DFS](checklist-tune-a-dfs-namespace.md)
-   [Репликация](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770278(v=ws.11))
