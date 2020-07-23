---
title: Репликация конечных объектов папок с помощью репликации DFS
description: В этой статье рассматривается, как реплицировать конечные объекты папок с помощью репликации DFS.
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 399d9915cccc5d66c2b25b1e9f51c30e37d8dff6
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966446"
---
# <a name="replicate-folder-targets-using-dfs-replication"></a>Репликация конечных объектов папок с помощью репликации DFS

> Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

Можно использовать репликацию DFS для синхронизации содержимого конечных объектов папок, чтобы пользователи видели одни и те же файлы вне зависимости от того, на какой конечный объект папки перенаправляется клиентский компьютер.

## <a name="to-replicate-folder-targets-using-dfs-replication"></a>Репликация конечных объектов папок с помощью репликации DFS

1.  Нажмите кнопку **Пуск**, укажите пункт **Администрирование**, а затем щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните правой кнопкой мыши папку, содержащую два или более конечных объекта, и выберите **Реплицировать папку**.

3.  Следуйте инструкциям в мастере репликации папок.

> [!NOTE]
> Изменения конфигурации не применяются немедленно ко всем членам, кроме случаев с использованием командлетов [Suspend-DfsReplicationGroup](/powershell/module/dfsr/suspend-dfsreplicationgroup?view=win10-ps) и [Sync-DfsReplicationGroup](/powershell/module/dfsr/sync-dfsreplicationgroup?view=win10-ps). Новую конфигурацию необходимо реплицировать во все контроллеры домена, и каждый член группы репликации должен опросить ближайший контроллер домена, чтобы получить изменения. Время, которое для этого потребуется, зависит от задержки репликации в службах каталогов Active Directory (AD DS) и большого интервала опроса (60 минут) для каждого члена. Чтобы немедленно запросить изменения конфигурации, откройте окно командной строки и введите следующую команду по одному разу для каждого члена группы репликации: <br /> dfsrdiag.exe PollAD /Member:DOMAIN\Server1
<br />
Чтобы сделать это из сеанса Windows PowerShell, используйте командлет [Update-DfsrConfigurationFromAD](/powershell/module/dfsr/update-dfsrconfigurationfromad?view=win10-ps), который был введен в Windows Server 2012 R2.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md)
-   [Репликация DFS](../dfs-replication/dfsr-overview.md)
