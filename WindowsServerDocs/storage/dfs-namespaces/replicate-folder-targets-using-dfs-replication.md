---
title: Репликация конечных объектов папок с помощью репликации DFS
description: В этой статье рассматривается, как реплицировать конечные объекты папок с помощью репликации DFS.
ms.date: 6/5/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 098ffd1a47891d2355742682a002f80dcfc59650
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59878085"
---
# <a name="replicate-folder-targets-using-dfs-replication"></a>Репликация конечных объектов папок с помощью репликации DFS

> Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

Можно использовать репликацию DFS для синхронизации содержимого конечных объектов папок, чтобы пользователи видели одни и те же файлы вне зависимости от того, на какой конечный объект папки перенаправляется клиентский компьютер.

## <a name="to-replicate-folder-targets-using-dfs-replication"></a>Репликация конечных объектов папок с помощью репликации DFS

1.  Нажмите кнопку **Пуск**, наведите курсор на **Администрирование** и щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните правой кнопкой мыши папку, содержащую два или более конечных объекта, и выберите **Реплицировать папку**.

3.  Следуйте инструкциям в мастере репликации папок.

> [!NOTE]
> Изменения конфигурации не применяются немедленно ко всем членам, кроме случаев с использованием командлетов [Suspend-DfsReplicationGroup](https://technet.microsoft.com/itpro/powershell/windows/dfsr/suspend-dfsreplicationgroup) и [Sync-DfsReplicationGroup](https://technet.microsoft.com/itpro/powershell/windows/dfsr/sync-dfsreplicationgroup). Новую конфигурацию необходимо реплицировать во все контроллеры домена, и каждый член группы репликации должен опросить ближайший контроллер домена, чтобы получить изменения. Это занимает время зависит от задержки репликации службы каталогов Active Directory (AD DS) и большого интервала опроса (60 минут) для каждого члена. Чтобы немедленно запросить изменения конфигурации, откройте окно командной строки и введите следующую команду по одному разу для каждого члена группы репликации: <br /> dfsrdiag.exe PollAD /Member:DOMAIN\Server1
<br />
Чтобы сделать это из сеанса Windows PowerShell, используйте [DfsrConfigurationFromAD обновления](https://technet.microsoft.com/itpro/powershell/windows/dfsr/update-dfsrconfigurationfromad) командлет, который появился в Windows Server 2012 R2.

## <a name="see-also"></a>См. также

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Делегирование разрешений на управление для пространства имен DFS](delegate-management-permissions-for-dfs-namespaces.md)
-   [Служба репликации DFS](../dfs-replication/dfsr-overview.md)