---
title: "Известные проблемы с репликой хранилища"
ms.prod: windows-server-threshold
manager: siroy
ms.author: nedpyle
ms.technology: storage-replica
ms.topic: get-started-article
author: nedpyle
ms.date: 10/13/2016
ms.assetid: ceddb0fa-e800-42b6-b4c6-c06eb1d4bc55
ms.openlocfilehash: 6f02ece1f327cf53667df09e6d13ace001259885
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="known-issues-with-storage-replica"></a>Известные проблемы с репликой хранилища

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе рассматриваются известные проблемы с репликой хранилища в Windows Server2016.  

## <a name="after-removing-replication-disks-are-offline-and-you-cannot-configure-replication-again"></a>После удаления репликации диски отключаются и для них невозможно снова настроить репликацию  
В Windows Server2016 может сложиться так, что вы не сможете подготовить репликацию для тома, который ранее реплицировался, или подключить некоторые тома. Такое происходит, если удаление репликации не было выполнено из-за ошибок, а также при повторной установке операционной системы на компьютер, который ранее реплицировал данные.  

Чтобы устранить эту проблему, необходимо очистить скрытый раздел реплики хранилища на всех дисках, вернув их в состояние пригодных для записи, с помощью командлета `Clear-SRMetadata`.  

-   Чтобы удалить все потерянные слоты баз данных реплики хранилища и снова подключить все разделы, используйте параметр `-AllPartitions`, вот так:  

    ```  
    Clear-SRMetadata -AllPartitions  
    ```  

-   Чтобы удалить данные журнала для всех потерянных реплик хранилища, используйте параметр `-AllLogs`, вот так:  

    ```  
    Clear-SRMetadata -AllLogs  
    ```  

-   Чтобы удалить потерянные данные настройки кластеров отработки отказа, используйте параметр `-AllConfiguration`, вот так:  

    ```  
    Clear-SRMetadata -AllConfiguration  
    ```  

-   Чтобы удалить отдельные метаданные групп репликации, используйте параметр `-Name` и укажите группу репликации, вот так:  

    ```  
    Clear-SRMetadata -Name RG01 -Logs -Partition  
    ```  

После очистки базы данных разделов может потребоваться перезагрузка сервера. Ее можно временно отложить, используя `-NoRestart`, но мы не рекомендуем пропускать перезапуск сервера, если ее предлагает командлет. Этот командлет не удаляет тома данных или данные в этих томах.  

## <a name="during-initial-sync-see-event-log-4004-warnings"></a>Во время начальной синхронизации вы видите предупреждения журнала событий4004  
В Windows Server2016 при настройке репликации для исходного и конечного серверов во время начальной синхронизации может отображаться множество предупреждений журнала событий4004 от **StorageReplica\Admin** с текстом состояния "Недостаточно системных ресурсов для завершения вызова API". Также вы можете увидеть несколько ошибок5014. Это означает, что у серверов недостаточный объем доступной памяти (ОЗУ) для одновременного выполнения начальной синхронизации и обычных рабочих нагрузок. Следует увеличить объем оперативной памяти либо уменьшить объем используемой памяти для всех компонентов и приложений, кроме реплики хранилища.  

## <a name="when-using-guest-clusters-with-shared-vhdx-and-a-host-without-a-csv-virtual-machines-stop-responding-after-configuring-replication"></a>При использовании гостевых кластеров с общим диском VHDX и узлом без CSV-файла виртуальные машины перестают отвечать после настройки репликации  
Если в Windows Server2016 для тестирования или демонстрации реплики хранилища используются гостевые кластеры Hyper-V, а в качестве хранилища гостевого кластера указан общий диск VHDX, виртуальные машины перестают отвечать после завершения настройки репликации. При перезапуске узла Hyper-V виртуальные машины начинают работать, но настройка на считается завершенной и репликация не выполняется.  

Такое происходит, если использовать **fltmc.exe присоединить svhdxflt** для обхода требования наличия CSV на узле Hyper-V. Использование этой команды не поддерживается. Она предназначена только для тестирования или демонстрации.  

Причиной замедления работы является естественная несогласованность взаимодействия между функцией качества обслуживания хранилища, появившейся в Windows Server2016, и добавленным вручную фильтром общих дисков VHDX. Чтобы устранить эту проблему, отключите драйвер фильтра качества обслуживания хранилища и перезапустите узел Hyper-V:  

```  
SC config storqosflt start= disabled  
```  

## <a name="cannot-configure-replication-when-using-new-volume-and-differing-storage"></a>Невозможно настроить репликацию для нового тома и другого хранилища  
Если при использовании командлета `New-Volume` указать разные наборы хранилищ для серверов источника и назначения, например два различных SAN или два JBOD с различными дисками, вы не сможете позднее настроить репликацию с помощью `New-SRPartnership`. Возможны разные сообщения об ошибках, например:  

    Data partition sizes are different in those two groups  

Для создания тома вместо `New-Volume` используйте командлет `New-Partition**`, а затем отформатируйте его. Первый из этих командлетов может округлять размера тома в разных массивах хранения данных. Если вы уже создали том NTFS, можно с помощью `Resize-Partition` увеличить или уменьшить размер одного тома, чтобы он в точности соответствовал другому (это невозможно для томов ReFS). При использовании **Diskmgmt** или **диспетчера сервера** округления не происходит.  

## <a name="running-test-srtopology-fails-with-name-related-errors"></a>Выполнение Test-SRTopology завершается ошибками, связанными с именами

При попытке использовать `Test-SRTopology` вы получите одну из следующих ошибок.  

**ПРИМЕР ОШИБКИ 1:**

    WARNING: Invalid value entered for target computer name: sr-srv03. Test-SrTopology cmdlet does not accept IP address as  
    input for target computer name parameter. NetBIOS names and fully qualified domain names are acceptable inputs  
    WARNING: System.Exception  
    WARNING:    at Microsoft.FileServices.SR.Powershell.TestSRTopologyCommand.BeginProcessing()  
    Test-SRTopology : Invalid value entered for target computer name: sr-srv03. Test-SrTopology cmdlet does not accept IP  
    address as input for target computer name parameter. NetBIOS names and fully qualified domain names are acceptable  
    inputs  
    At line:1 char:1  
    + Test-SRTopology -SourceComputerName sr-srv01 -SourceVolumeName d: -So ...  
    + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  
        + CategoryInfo          : InvalidArgument: (:) [Test-SRTopology], Exception  
        + FullyQualifiedErrorId : TestSRTopologyFailure,Microsoft.FileServices.SR.Powershell.TestSRTopologyCommand  

**ПРИМЕР ОШИБКИ 2:**

    WARNING: Invalid value entered for source computer name

**ПРИМЕР ОШИБКИ 3:**

    The specified volume cannot be found G: cannot be found on computer SRCLUSTERNODE1

Этот командлет использует ограниченные функции отчетов об ошибках в Windows Server2016 и поэтому возвращает одинаковые выходные данные для многих распространенных проблем. Такая ошибка может возникнуть по следующим причинам:  

* вы вошли на исходный компьютер как локальный пользователь, а не как пользователь домена;  
* конечный компьютер не работает или не доступен по сети;  
* указано неправильное имя конечного компьютера;  
* указан IP-адрес вместо имени конечного компьютера;  
* брандмауэр на конечном компьютере блокирует доступ для вызовов PowerShell или CIM;  
* на конечном компьютере не работает служба WMI;   
* при выполнении командлета `Test-SRTopology` с удаленного компьютера управления вы не применили CREDSSP.
* Указанные тома источника или назначения являются локальными дисками на узле кластера, а не кластерными дисками.  

## <a name="configuring-new-storage-replica-partnership-returns-an-error---failed-to-provision-partition"></a>При настройке нового партнерства реплики хранилища возвращается сообщение об ошибке "Не удалось подготовить к работе раздел"
При попытке создать новое партнерство репликации с помощью `New-SRPartnership` вы получаете следующую ошибку:

    New-SRPartnership : Unable to create replication group test01, detailed reason: Failed to provision partition ed0dc93f-107c-4ab4-a785-afd687d3e734.
    At line: 1 char: 1
    + New-SRPartnership -SourceComputerName srv1 -SourceRGName test01
    + Categorylnfo : ObjectNotFound: (MSFT_WvrAdminTasks : root/ Microsoft/. . s) CNew-SRPartnership], CimException
    + FullyQua1ifiedErrorId : Windows System Error 1168 ,New-SRPartnership

Это происходит, если выбран том данных на том же разделе, где расположен системный диск (диск **C:** и папка Windows). Например, если один диск содержит оба тома **C:** и **D:**, созданные в одном разделе. Реплика хранилища не поддерживает такую возможность. Необходимо выбрать другой том для репликации.

## <a name="attempting-to-grow-a-replicated-volume-fails-due-to-missing-update"></a>Не удается увеличить размер реплицированного тома из-за отсутствующего обновления
При попытке увеличения или расширения реплицированного тома возникает следующая ошибка:

    PS C:\> Resize-Partition -DriveLetter d -Size 44GB
    Resize-Partition : The operation failed with return code 8
    At line:1 char:1
    + Resize-Partition -DriveLetter d -Size 44GB
    + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (StorageWMI:ROOT/Microsoft/.../MSFT_Partition
    [Resize-Partition], CimException
    + FullyQualifiedErrorId : StorageWMI 8,Resize-Partition

При использовании оснастки консоли MMC "Управление дисками" появляется эта ошибка: 

    Element not found

Она появляется, даже если вы правильно включили изменение размера тома на исходном сервере с помощью параметра `Set-SRGroup -Name rg01 -AllowVolumeResize $TRUE`. 

Эта проблема была устранена в накопительном пакете обновления для Windows 10 версии 1607 и Windows Server 2016: 9 декабря 2016 г. (KB3201845). 

## <a name="attempting-to-grow-a-replicated-volume-fails-due-to-missing-step"></a>Не удается увеличить размер реплицированного тома из-за пропущенного действия
Если вы попытаетесь изменить размер реплицированного тома на исходном сервере, предварительно не установив `-AllowResizeVolume $TRUE`, то возникнут следующие ошибки:

    PS C:\> Resize-Partition -DriveLetter I -Size 8GB
    Resize-Partition : Failed
    Activity ID: {87aebbd6-4f47-4621-8aa4-5328dfa6c3be}
    At line:1 char:1
    + Resize-Partition -DriveLetter I -Size 8GB
    + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
        + CategoryInfo          : NotSpecified: (StorageWMI:ROOT/Microsoft/.../MSFT_Partition) [Resize-Partition], CimException
        + FullyQualifiedErrorId : StorageWMI 4,Resize-Partition

Ошибка журнала событий реплики хранилища 10307:

    Attempted to resize a partition that is protected by Storage Replica .

    DeviceName: \Device\Harddisk1\DR1
    PartitionNumber: 7
    PartitionId: {b71a79ca-0efe-4f9a-a2b9-3ed4084a1822}

    Guidance: To grow a source data partition, set the policy on the replication group containing the data partition.

    Set-SRGroup -ComputerName [ComputerName] -Name [ReplicationGroupName] -AllowVolumeResize $true

    Before you grow the source data partition, ensure that the destination data partition has enough space to grow to an equal size. Shrinking of data partition protected by Storage Replica is blocked.

Ошибка оснастки "Управление дисками": 

    An unexpected error has occurred 

После изменения размера тома не забудьте отключить изменение размера с помощью параметра `Set-SRGroup -Name rg01 -AllowVolumeResize $FALSE`. После этого администраторы не смогут изменить размеры томов, не убедившись, что на целевом томе достаточно места, обычно они не знают о реплике хранилища. 

## <a name="attempting-to-move-a-pdr-resource-between-sites-on-an-asynchronous-stretch-cluster-fails"></a>Не удается переместить ресурс PDR между сайтами в асинхронном растянутом кластере
При попытке переместить присоединенную к ресурсу роль физического диска, например файловый сервер для общего использования, чтобы переместить связанное хранилище в асинхронный растянутый кластер, возникает ошибка.

При использовании оснастки диспетчера отказоустойчивости кластеров:

    Error
    The operation has failed.
    The action 'Move' did not complete.
    Error Code: 0x80071398
    The operation failed because either the specified cluster node is not the owner of the group, or the node is not a possible owner of the group
    
При использовании командлета PowerShell кластера:

    PS C:\> Move-ClusterGroup -Name sr-fs-006 -Node sr-srv07
    Move-ClusterGroup : An error occurred while moving the clustered role 'sr-fs-006'.
    The operation failed because either the specified cluster node is not the owner of the group, or the node is not a
    possible owner of the group
    At line:1 char:1
    + Move-ClusterGroup -Name sr-fs-006 -Node sr-srv07
    + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Move-ClusterGroup], ClusterCmdletException
    + FullyQualifiedErrorId : Move-ClusterGroup,Microsoft.FailoverClusters.PowerShell.MoveClusterGroupCommand

Это происходит из-за ожидаемого поведения Windows Server 2016. Используйте `Set-SRPartnership` для перемещения этих дисков PDR в асинхронный растянутый кластер.  

## <a name="attempting-to-add-disks-to-a-two-node-asymmetric-cluster-returns-no-disks-suitable-for-cluster-disks-found"></a>При попытке добавить диски в асимметричный кластер с двумя узлами отображается сообщение "Не найдены диски, подходящие для дисков кластера" 
При попытке подготовить кластер только с двумя узлами перед добавлением растянутой репликации для реплики хранилища предпринимается попытка добавить диски в раздел "Доступные диски" на втором сайте. Вы увидите следующую ошибку:

    "No disks suitable for cluster disks found. For diagnostic information about disks available to the cluster, use the Validate a Configuration Wizard to run Storage tests." 

Этого не происходит, если в кластере не менее трех узлов. Ошибка возникает из-за намеренного изменения кода вWindows Server2016 на случай асимметричной кластеризации хранилища. 

Чтобы добавить хранилище, необходимо выполнить следующую команду на узле второго сайта:

`Get-ClusterAvailableDisk -All | Add-ClusterDisk`

Это не будет работать с локальным хранилищем узла. Можно использовать реплику хранилища, чтобы реплицировать растянутый кластер между двумя узлами, **на каждом из которых используется свой собственный набор общих хранилищ.** 

## <a name="the-smb-bandwidth-limiter-fails-to-throttle-storage-replica-bandwidth"></a>Механизму ограничения пропускной способности в протоколе SMB не удается регулировать пропускную способность реплики хранилища
При указании ограничение пропускной способности реплики хранилища оно игнорируется, и используется полная пропускная способность. Например:

`Set-SmbBandwidthLimit  -Category StorageReplication -BytesPerSecond 32MB`

Эта проблема возникает из-за ошибки совместимости реплики хранилища и SMB. Эта проблема была исправлена в накопительном обновлении Windows Server 2016 от июля 2017 г. и в Windows Server версии 1709.

## <a name="event-1241-warning-repeated-during-initial-sync"></a>Предупреждение о событии 1241 повторяется во время исходной синхронизации
Хотя партнерство репликации указывается асинхронно, на исходном компьютере несколько раз регистрируется предупреждение (событие 1241) в канале администратора реплики хранилища. Например:

    Log Name:      Microsoft-Windows-StorageReplica/Admin
    Source:        Microsoft-Windows-StorageReplica
    Date:          3/21/2017 3:10:41 PM
    Event ID:      1241
    Task Category: (1)
    Level:         Warning
    Keywords:      (1)
    User:          SYSTEM
    Computer:      sr-srv05.corp.contoso.com
    Description:
    The Recovery Point Objective (RPO) of the asynchronous destination is unavailable.

    LocalReplicationGroupName: rg01
    LocalReplicationGroupId: {e20b6c68-1758-4ce4-bd3b-84a5b5ef2a87}
    LocalReplicaName: f:\
    LocalPartitionId: {27484a49-0f62-4515-8588-3755a292657f}
    ReplicaSetId: {1f6446b5-d5fd-4776-b29b-f235d97d8c63}
    RemoteReplicationGroupName: rg02
    RemoteReplicationGroupId: {7f18e5ea-53ca-4b50-989c-9ac6afb3cc81}
    TargetRPO: 30

    Guidance: This is typically due to one of the following reasons: 

В настоящее время асинхронный получатель отсоединен. RPO может стать доступной после восстановления подключения.

    The asynchronous destination is unable to keep pace with the source such that the most recent destination log record is no longer present in the source log. The destination will start block copying. The RPO should become available after block copying completes.

Такое поведение во время исходной синхронизации не является, его можно игнорировать. Такое поведение может измениться в более поздней версии. Если вы наблюдаете такое поведение во время текущей асинхронной репликации, изучите партнерство, чтобы определить, почему репликация выходит за пределы настроенной RPO (по умолчанию 30 секунд).

## <a name="event-4004-warning-repeated-after-rebooting-a-replicated-node"></a>Предупреждение о событии 4004 повторяется после перезагрузки узла репликации
В редких и обычно невоспроизводимых обстоятельствах перезагрузка сервера, который находится в отношениях партнерства, приводит к сбою репликации с регистрацией предупреждения 4004 и ошибкой доступа на перезагруженном узле.

    Log Name:      Microsoft-Windows-StorageReplica/Admin
    Source:        Microsoft-Windows-StorageReplica
    Date:          3/21/2017 11:43:25 AM
    Event ID:      4004
    Task Category: (7)
    Level:         Warning
    Keywords:      (256)
    User:          SYSTEM
    Computer:      server.contoso.com
    Description:
    Failed to establish a connection to a remote computer.

    RemoteComputerName: server
    LocalReplicationGroupName: rg01
    LocalReplicationGroupId: {a386f747-bcae-40ac-9f4b-1942eb4498a0}
    RemoteReplicationGroupName: rg02
    RemoteReplicationGroupId: {a386f747-bcae-40ac-9f4b-1942eb4498a0}
    ReplicaSetId: {00000000-0000-0000-0000-000000000000}
    RemoteShareName:{a386f747-bcae-40ac-9f4b-1942eb4498a0}.{00000000-0000-0000-0000-000000000000}
    Status: {Access Denied}
    A process has requested access to an object, but has not been granted those access rights.

    Guidance: Possible causes include network failures, share creation failures for the remote replication group, or firewall settings. Make sure SMB traffic is allowed and there are no connectivity issues between the local computer and the remote computer. You should expect this event when suspending replication or removing a replication partnership.

Обратите внимание на состояние `Status: "{Access Denied}"` и сообщение `A process has requested access to an object, but has not been granted those access rights.` Это известная проблема реплики хранилища, исправленная в обновлении качества от 12 сентября 2017 г.— KB4038782 (сборка ОС 14393.1715) https://support.microsoft.com/en-us/help/4038782/windows-10-update-kb4038782 

## <a name="error-failed-to-bring-the-resource-cluster-disk-x-online-with-a-stretch-cluster"></a>Ошибка «Не удалось подключить ресурс "Диск кластера x" к сети». для растянутого кластера
При подключении диска кластера после успешной отработки отказа, когда вы пытаетесь снова сделать исходный сайт основным, возникает ошибка диспетчера отказоустойчивого кластера. Например:

    Error
    The operation has failed.
    Failed to bring the resource 'Cluster Disk 2' online.
    
    Error Code: 0x80071397
    The operation failed because either the specified cluster node is not the owner of the resource, or the node is not a possible owner of the resource.
    
Если вы попытаетесь переместить диск или CSV вручную, возникает другая ошибка. Например:

    Error
    The operation has failed.
    The action 'Move' did not complete.
    
    Error Code: 0x8007138d
    A cluster node is not available for this operation

Эта проблема вызвана тем, что один или несколько неинициализированных дисков подключены к одному или нескольким узлам кластера. Для решения проблемы инициализируйте все подключенные ресурсы хранилища с помощью DiskMgmt.msc, DISKPART.EXE или командлета PowerShell Initialize-Disk.

Мы работаем над обновлением, в котором эта проблема будет полностью устранена. Если вы хотите нам помочь и у вас есть соглашение о поддержке Microsoft Premier, напишите по адресу SRFEED@microsoft.com, чтобы мы вместе могли создать запрос на применение исправления предыдущей версии.

## <a name="gpt-error-when-attempting-to-create-a-new-sr-partnership"></a>Ошибка GPT при попытке создать партнерство SR

При выполнении командлета New-SRPartnership возникает ошибка: 

    Disk layout type for volume \\?\Volume{GUID}\ is not a valid GPT style layout.
    New-SRPartnership : Unable to create replication group SRG01, detailed reason: Disk layout type for volume
    \\?\Volume{GUID}\ is not a valid GPT style layout.
    At line:1 char:1
    + New-SRPartnership -SourceComputerName nodesrc01 -SourceRGName SRG01 ...
    + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo : NotSpecified: (MSFT_WvrAdminTasks:root/Microsoft/...T_WvrAdminTasks) [New-SRPartnership]
    , CimException
    + FullyQualifiedErrorId : Windows System Error 5078,New-SRPartnership

В графическом интерфейсе диспетчера отказоустойчивого кластера нет параметра для настройки репликации диска.

При выполнении командлета Test-SRTopology возникает ошибка: 

    WARNING: Object reference not set to an instance of an object.
    WARNING: System.NullReferenceException
    WARNING:    at Microsoft.FileServices.SR.Powershell.MSFTPartition.GetPartitionInStorageNodeByAccessPath(String AccessPath, String ComputerName, MIObject StorageNode)
       at Microsoft.FileServices.SR.Powershell.Volume.GetVolume(String Path, String ComputerName)
       at Microsoft.FileServices.SR.Powershell.TestSRTopologyCommand.BeginProcessing()
    Test-SRTopology : Object reference not set to an instance of an object.
    At line:1 char:1
    + Test-SRTopology -SourceComputerName nodesrc01 -SourceVolumeName U: - ...
    + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo : InvalidArgument: (:) [Test-SRTopology], NullReferenceException
    + FullyQualifiedErrorId : TestSRTopologyFailure,Microsoft.FileServices.SR.Powershell.TestSRTopologyCommand 

Это вызвано тем, что функциональный уровень кластера по-прежнему настроен как Windows Server 2012 R2 (т. е. FL 8). Хранилище реплики должно возвращать определенную ошибку, но вместо этого возвращает неверное сопоставление ошибки.

Выполните командлет Get-Cluster | fl * на каждом узле.

Если ClusterFunctionalLevel = 9, для реализации реплики хранилища на узле требуется версия Windows ClusterFunctionalLevel 2016.
Если значение ClusterFunctionalLevel отличается от 9, свойство ClusterFunctionalLevel необходимо обновить для реализации реплики хранилища на этом узле.

Чтобы устранить проблему, повысить функциональный уровень кластера, выполнив командлет PowerShell: Update-ClusterFunctionalLevel https://technet.microsoft.com/itpro/powershell/windows/failoverclusters/update-clusterfunctionallevel

## <a name="small-unknown-partition-listed-in-diskmgmt-for-each-replicated-volume"></a>Небольшой неизвестный раздел, указанный в DISKMGMT для реплицированного тома

При запуске оснастки "Управление дисками" (DISKMGMT.MSC) вы заметите один или несколько томов, указанных без ярлыка или буквы диска и с размером 1 МБ. Вы сможете удалить неизвестный том или вы можете получить:

    "An Unexpected Error has Occurred"  

Это поведение реализовано намеренно. Это не том, а раздел. Реплика хранилища создает раздел размером 512 КБ как слот базы данных для операций репликации (устаревшее средство DiskMgmt.msc округляется до ближайшего размера в МБ). Наличие раздела, подобного этому, для каждого реплицированного тома является нормальным и желательным. Если этот раздел размером 512 КБ больше не используется, его можно удалить. Разделы, которые используются, удалять нельзя. Раздел никогда не увеличится и не уменьшится. Если вы повторно создаете репликацию, мы рекомендуем оставить раздел, так как реплика хранилища будет требовать неиспользуемые разделы.

Для просмотра сведений используйте средство DISKPART или командлет Get-Partition. Эти разделы будут иметь тип GPT `558d43c5-a1ac-43c0-aac8-d1472b2923d1`. 

## <a name="see-also"></a>См. также:  
- [Реплика хранилища](storage-replica-overview.md)  
- [Репликация растянутого кластера с помощью общего хранилища](stretch-cluster-replication-using-shared-storage.md)  
- [Репликация с сервера в хранилище сервера](server-to-server-storage-replication.md)  
- [Межкластерная репликация хранилища](cluster-to-cluster-storage-replication.md)  
- [Часто задаваемые вопросы о реплике хранилища](storage-replica-frequently-asked-questions.md)  
- [Локальные дисковые пространства](../storage-spaces/storage-spaces-direct-overview.md)  
