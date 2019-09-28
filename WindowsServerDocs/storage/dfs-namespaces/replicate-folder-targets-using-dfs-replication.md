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
ms.openlocfilehash: ad26b8685539869e9302eafac69df19d11778a1b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386131"
---
# <a name="replicate-folder-targets-using-dfs-replication"></a>Репликация конечных объектов папок с помощью репликации DFS

> Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

Можно использовать репликацию DFS для синхронизации содержимого конечных объектов папок, чтобы пользователи видели одни и те же файлы вне зависимости от того, на какой конечный объект папки перенаправляется клиентский компьютер.

## <a name="to-replicate-folder-targets-using-dfs-replication"></a>Репликация конечных объектов папок с помощью репликации DFS

1.  Нажмите кнопку **Пуск**, наведите курсор на **Администрирование** и щелкните **Управление DFS**.

2.  В узле **Пространства имен** дерева консоли щелкните правой кнопкой мыши папку, содержащую два или более конечных объекта, и выберите **Реплицировать папку**.

3.  Следуйте инструкциям в мастере репликации папок.

> [!NOTE]
> Изменения конфигурации не применяются немедленно ко всем членам, кроме случаев с использованием командлетов [Suspend-DfsReplicationGroup](https://technet.microsoft.com/itpro/powershell/windows/dfsr/suspend-dfsreplicationgroup) и [Sync-DfsReplicationGroup](https://technet.microsoft.com/itpro/powershell/windows/dfsr/sync-dfsreplicationgroup). Новую конфигурацию необходимо реплицировать во все контроллеры домена, и каждый член группы репликации должен опросить ближайший контроллер домена, чтобы получить изменения. Время, необходимое для этого, зависит от задержки репликации служб Active Directory Directory (AD DS) и длительного интервала опроса (60 минут) для каждого участника. Чтобы немедленно запросить изменения конфигурации, откройте окно командной строки и введите следующую команду по одному разу для каждого члена группы репликации: <br /> dfsrdiag.exe PollAD /Member:DOMAIN\Server1
<br />
Чтобы сделать это из сеанса Windows PowerShell, используйте командлет [Update-дфсрконфигуратионфромад](https://technet.microsoft.com/itpro/powershell/windows/dfsr/update-dfsrconfigurationfromad) , который появился в Windows Server 2012 R2.

## <a name="see-also"></a>См. также

-   [Развертывание пространств имен DFS](deploying-dfs-namespaces.md)
-   [Делегирование прав управления пространствами имен DFS](delegate-management-permissions-for-dfs-namespaces.md)
-   [Репликация DFS](../dfs-replication/dfsr-overview.md)