---
title: Прямые дисковые пространства Устранение неполадок службы хранилища
description: Узнайте, как устранять неполадки развернутой дисковыми пространствами.
keywords: Дисковые пространства
ms.prod: windows-server-threshold
ms.author: ''
ms.technology: storage-spaces
ms.topic: article
author: kaushika-msft
ms.date: 10/24/2018
ms.localizationpriority: medium
ms.openlocfilehash: 44bcf48f3e4a3b4b49ff027d3aa3e5704865e7b5
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66447884"
---
# <a name="troubleshoot-storage-spaces-direct"></a>Устранение неполадок Storage Spaces Direct

> Относится к: Windows Server 2019, Windows Server 2016

Используйте следующие сведения для устранения неполадок дисковых развертывания.

Как правило запустите, выполнив следующие действия:

1. Убедитесь, что изготовитель/модель SSD сертифицирован для Windows Server 2016 и Windows Server 2019 г. с помощью каталог Windows Server. С помощью поставщика можно Подтвердите, что диски поддерживаются для дисковых пространств.
2. Проверьте хранилище для всех неисправных дисков. Используйте программное обеспечение для управления хранилища, чтобы проверить состояние дисков. Если какой-либо из дисков, неисправен, обратитесь к поставщику. 
3. Обновление хранилища и встроенного по диска, при необходимости.
   Убедитесь, что на всех узлах установлены последние обновления Windows. Можно получить последние обновления для Windows Server 2016 из [Журнал обновлений Windows 10 и Windows Server 2016](https://aka.ms/update2016) и для Windows Server 2019 из [Журнал обновлений Windows 10 и Windows Server 2019](https://support.microsoft.com/help/4464619).
4. Обновите драйверы сетевого адаптера и встроенного по.
5. Запустите проверку кластера и просмотрите раздел "пространства дисковыми" Проверьте, правильно выводятся те диски, которые будут использоваться для кэша и без ошибок.

Если вас по-прежнему возникают проблемы, просмотрите приведенные ниже.

## <a name="virtual-disk-resources-are-in-no-redundancy-state"></a>Виртуальный диск ресурсы находятся в состоянии без избыточности
Узлы дисковые системы неожиданно перезапускаться из-за аварийного завершения или сбое питания. Выберите один или несколько виртуальных дисков не подключается, и вы увидите описание «недостаточно избыточности информация».

|FriendlyName|ResiliencySettingName| OperationalStatus| HealthStatus| IsManualAttach|Размер| PSComputerName|
|------------|---------------------| -----------------| ------------| --------------|-----| --------------|
|Disk4| Зеркальное отображение| ОК|  Работоспособное| True|  10 ТБ|  Узел 01.conto...|
|Диск 3         |Зеркальное отображение                 |ОК                          |Работоспособное       |True            |10 ТБ | Узел 01.conto...|
|Диски 2         |Зеркальное отображение                 |Без резервирования               |Unhealthy     |True            |10 ТБ | Узел 01.conto...|
|Диск 1         |Зеркальное отображение                 |{Не избыточности, InService}  |Unhealthy     |True            |10 ТБ | Узел 01.conto...| 

Кроме того после попытки подключить виртуальный диск, следующие сведения регистрируется в журнале кластера (DiskRecoveryAction).  

```
[Verbose] 00002904.00001040::YYYY/MM/DD-12:03:44.891 INFO [RES] Physical Disk <DiskName>: OnlineThread: SuGetSpace returned 0.
[Verbose] 00002904.00001040:: YYYY/MM/DD -12:03:44.891 WARN [RES] Physical Disk < DiskName>: Underlying virtual disk is in 'no redundancy' state; its volume(s) may fail to mount.
[Verbose] 00002904.00001040:: YYYY/MM/DD -12:03:44.891 ERR [RES] Physical Disk <DiskName>: Failing online due to virtual disk in 'no redundancy' state. If you would like to attempt to online the disk anyway, first set this resource's private property 'DiskRecoveryAction' to 1. We will try to bring the disk online for recovery, but even if successful, its volume(s) or CSV may be unavailable. 
``` 

**Нет избыточности оперативное состояние** может произойти, если диск не удалось, или если система не может получить доступ к данным на виртуальном диске. Эта проблема может возникать, если на узле происходит перезагрузка во время обслуживания на узлах.

Чтобы устранить эту проблему, выполните следующие действия.

1. Удалите затронутые виртуальные диски из CSV-файла. Это будет поместить их в группу «Доступное хранилище» в кластере и отображение как ResourceType «Физический диск».

   ```powershell
   Remove-ClusterSharedVolume -name "VdiskName"
   ``` 
2. На узле, принадлежащем доступной группе хранения выполните следующую команду на каждом диске, который находится в состоянии без избыточности. Для идентификации узла в группу «Доступное хранилище» именно вы можете выполните следующую команду.

   ```powershell
   Get-ClusterGroup
   ```
3. Задайте действие восстановления диска, а затем запустите диски.
   ```powershell
   Get-ClusterResource "VdiskName" | Set-ClusterParameter -Name DiskRecoveryAction -Value 1
   Start-ClusterResource -Name "VdiskName"
   ```
4. Восстановление начнется автоматически. Дождитесь завершения восстановления. Он может перейти в приостановленное состояние и начать заново. Чтобы отслеживать ход выполнения: 
    - Запустите **Get-StorageJob** для мониторинга состояния восстановления и см. в разделе после его завершения.
    - Запустите **Get-VirtualDisk** и убедитесь, что пространство возвращает HealthStatus из исправное состояние.
5. После исправления завершения и виртуальные диски являются работоспособное состояние, изменение параметров виртуального диска обратно.

   ```powershell
    Get-ClusterResource "VdiskName" | Set-ClusterParameter -Name DiskRecoveryAction -Value 0
   ```
6. Выполните дисков и затем автономный еще раз, чтобы иметь DiskRecoveryAction вступили в силу.

   ```powershell
   Stop-ClusterResource "VdiskName"
   Start-ClusterResource "VdiskName"
   ``` 
7. Добавьте затронутые виртуальные диски обратно в CSV-ФАЙЛ.

   ```powershell
   Add-ClusterSharedVolume -name "VdiskName"
   ```

**DiskRecoveryAction** параметр переопределения, позволяющим подключать том пространства в режиме чтения и записи без каких-либо проверок. Свойство позволяет выполнять диагностику в почему тома не переходит в оперативный режим. Это очень похоже на режим обслуживания, но его можно вызвать для ресурса в состоянии сбоя. Это также позволяет получить доступ к данным, что может быть полезно в ситуациях, например «Нет избыточности, «где можно получить доступ к любые данные можно и скопировать его. Свойство DiskRecoveryAction была добавлена в 22 февраля 2018 г, обновления, 4077525 КБ.


## <a name="detached-status-in-a-cluster"></a>Состояние отсоединенных в кластере 

При запуске **Get-VirtualDisk** командлета, свойство operationalstatus имеет значение для одного или нескольких дисковыми пространствами виртуальных дисков отсоединяется. Тем не менее, сообщаемое HealthStatus **Get-PhysicalDisk** командлет указывает, что все физические диски находятся в работоспособном состоянии.

Ниже приведен пример выходных данных из **Get-VirtualDisk** командлета.

|FriendlyName|  ResiliencySettingName|  OperationalStatus|   HealthStatus|  IsManualAttach|  Размер|   PSComputerName|
|-|-|-|-|-|-|-|
|Disk4|         Зеркальное отображение|                 ОК|                  Работоспособное|       True|            10 ТБ|  Узел 01.conto...|
|Диск 3|         Зеркальное отображение|                 ОК|                  Работоспособное|       True|            10 ТБ|  Узел 01.conto...|
|Диски 2|         Зеркальное отображение|                 "Detached" (отключено)|            Неизвестно|       True|            10 ТБ|  Узел 01.conto...|
|Диск 1|         Зеркальное отображение|                 "Detached" (отключено)|            Неизвестно|       True|            10 ТБ|  Узел 01.conto...| 


Кроме того следующие события могут регистрироваться на узлах:

```
Log Name: Microsoft-Windows-StorageSpaces-Driver/Operational
Source: Microsoft-Windows-StorageSpaces-Driver 
Event ID: 311 
Level: Error
User: SYSTEM 
Computer: Node#.contoso.local 
Description: Virtual disk {GUID} requires a data integrity scan.  

Data on the disk is out-of-sync and a data integrity scan is required. 

To start the scan, run the following command:   
Get-ScheduledTask -TaskName "Data Integrity Scan for Crash Recovery" | Start-ScheduledTask                

Once you have resolved the condition listed above, you can online the disk by using the following commands in PowerShell:   

Get-VirtualDisk | ?{ $_.ObjectId -Match "{GUID}" } | Get-Disk | Set-Disk -IsReadOnly $false 
Get-VirtualDisk | ?{ $_.ObjectId -Match "{GUID}" } | Get-Disk | Set-Disk -IsOffline  $false
------------------------------------------------------------

Log Name: System
Source: Microsoft-Windows-ReFS 
Event ID: 134
Level: Error 
User: SYSTEM
Computer: Node#.contoso.local 
Description: The file system was unable to write metadata to the media backing volume <VolumeId>. A write failed with status "A device which does not exist was specified." ReFS will take the volume offline. It may be mounted again automatically.
------------------------------------------------------------
Log Name: Microsoft-Windows-ReFS/Operational
Source: Microsoft-Windows-ReFS 
Event ID: 5 
Level: Error 
User: SYSTEM 
Computer: Node#.contoso.local 
Description: ReFS failed to mount the volume. 
Context: 0xffffbb89f53f4180 
Error: A device which does not exist was specified.
Volume GUID:{00000000-0000-0000-0000-000000000000} 
DeviceName: 
Volume Name:
``` 

**Отсоединенных оперативное состояние** может произойти, если "грязных" областей (DRT) отслеживания журнал заполнен. Дисковых пространств использует "грязных" областей, отслеживания для зеркальных областей (DRT), чтобы убедиться в том, что при возникновении сбоя электропитания, любые активные обновления метаданных вошли на убедитесь в том, что дискового пространства можно вернуть или отмены операций, чтобы вернуть в дисковом пространстве в гибкой и согласованное состояние, после восстановления питания и система возобновляет работу. При заполнении журнала DRT виртуальный диск не удается подключить пока синхронизируются метаданные DRT и записаны на диск. Этот процесс требует выполнении полной проверки, что может занять несколько часов.

Чтобы устранить эту проблему, выполните следующие действия.
1. Удалите затронутые виртуальные диски из CSV-файла.

   ```powershell
   Remove-ClusterSharedVolume -name "VdiskName"
   ``` 
2. Выполните следующие команды на каждый диск, не возвращается в оперативный режим. 

   ```powershell
   Get-ClusterResource -Name "VdiskName" | Set-ClusterParameter DiskRunChkDsk 7
   Start-ClusterResource -Name "VdiskName"
   ``` 
3. Выполните следующую команду на каждом узле, в котором отсоединить том находится в сети. 

   ```powershell
   Get-ScheduledTask -TaskName "Data Integrity Scan for Crash Recovery" | Start-ScheduledTask 
   ```
   Эту задачу следует запустить на всех узлах, на которых работает отсоединенных тома. Восстановление начнется автоматически. Дождитесь завершения восстановления. Он может перейти в приостановленное состояние и начать заново. Чтобы отслеживать ход выполнения: 
   - Запустите **Get-StorageJob** для мониторинга состояния восстановления и см. в разделе после его завершения.
   - Запустите **Get-VirtualDisk** и проверьте пространство возвращает HealthStatus из исправное состояние.
     - «Данные целостности сканирования для Crash Recovery» является задачу, которая не отображается как задание хранилища, и нет нет индикатора выполнения. Если задача отображается как запущенные, он выполняется. После завершения, также будет показано завершенное.

       Кроме того можно просмотреть состояние выполнения запланированной задачи, используя следующий командлет: 
       ```powershell
       Get-ScheduledTask | ? State -eq running
       ``` 
4. Сразу же после «данных целостности сканирования для аварийных завершений» окончания восстановления, завершения восстановления и виртуальные диски являются работоспособное состояние, изменение параметров виртуального диска обратно. 

   ```powershell
   Get-ClusterResource -Name "VdiskName" | Set-ClusterParameter DiskRunChkDsk 0 
   ```
5. Добавьте затронутые виртуальные диски обратно в CSV-ФАЙЛ.    

   ```powershell
   Add-ClusterSharedVolume -name "VdiskName"
   ```  
   **Значение DiskRunChkdsk 7** используется для присоединения пространства тома и иметь секции в режиме только для чтения. Это позволяет пробелы самим находить и автоматически восстановить этот, запуская процесс восстановления. REPAIR будет выполняться автоматически один раз подключить. Он также дает возможность доступа к данным, которые могут оказаться полезными для получения доступа к любые данные, вы можете скопировать. Для некоторых условий сбоя, например в полном журнале DRT необходимо запустить проверки целостности данных для запланированной задачи восстановление после сбоя.

**Проверки целостности данных для задачи восстановление после сбоя** используется для синхронизации и очистить журнал отслеживания (DRT) полной "грязных" областей. Эта задача может занять несколько часов. «Данные целостности сканирования для Crash Recovery» является задачу, которая не отображается как задание хранилища, и нет нет индикатора выполнения. Если задача отображается как запущенные, он выполняется. После завершения, она будет отображаться как завершена. Если отменить задачу или перезапуск узла во время выполнения этой задачи, задачи необходимо начать заново с самого начала.

Дополнительные сведения см. в разделе [Устранение неполадок дисковыми пространствами работоспособности и состояния работоспособности](storage-spaces-states.md).

## <a name="event-5120-with-statusiotimeout-c00000b5"></a>Событие 5120 с STATUS_IO_TIMEOUT c00000b5 

> [!Important]
> **Для Windows Server 2016:** Чтобы уменьшить вероятность возникновения этих проблем во время применения обновлений с исправлением, рекомендуется установить с помощью следующей процедуры режима обслуживания хранилища [18 октября 2018 г., накопительное обновление для Windows Server 2016](https://support.microsoft.com/help/4462928)или более поздней версии, когда узлы уже установленной накопительное обновление Windows Server 2016, выпущенное из [8 мая 2018 г.](https://support.microsoft.com/help/4103723) для [9 октября 2018 г.](https://support.microsoft.com/help/KB4462917).

Может появиться событие 5120 с STATUS_IO_TIMEOUT c00000b5 после перезагрузки узла в Windows Server 2016 с накопительным пакетом обновления, вышедшие из [8 мая 2018 г. КБ 4103723](https://support.microsoft.com/help/4103723) для [9 октября 2018 г. КБ 4462917](https://support.microsoft.com/help/4462917)установлен.

При перезапуске узла 5120 событие регистрируется в журнале событий системы и включает в себя один из следующих кодов ошибки:

```
Event Source: Microsoft-Windows-FailoverClustering
Event ID: 5120
Description:    Cluster Shared Volume 'CSVName' ('Cluster Virtual Disk (CSVName)') has entered a paused state because of 'STATUS_IO_TIMEOUT(c00000b5)'. All I/O will temporarily be queued until a path to the volume is reestablished. 

Cluster Shared Volume ‘CSVName’ ('Cluster Virtual Disk (CSVName)') has entered a paused state because of 'STATUS_CONNECTION_DISCONNECTED(c000020c)'. All I/O will temporarily be queued until a path to the volume is reestablished.    
```

При регистрации событий 5120 динамической дамп создается для сбора данных об отладке, который может вызвать Дополнительные признаки или влиять на производительность. Создание динамической дампа создает небольшой паузы для включения создания моментального снимка памяти для записи файла дампа. Систем, которые имеют большой объем памяти и в условиях высокой нагрузки может привести к узлов для удаления из принадлежности к кластеру и также вызывают следующие 1135 событий должно быть записано в журнал.

```
Event source: Microsoft-Windows-FailoverClustering
Event ID: 1135  
Description: Cluster node 'NODENAME'was removed from the active failover cluster membership. The Cluster service on this node may have stopped. This could also be due to the node having lost communication with other active nodes in the failover cluster. Run the Validate a Configuration wizard to check your network configuration. If the condition persists, check for hardware or software errors related to the network adapters on this node. Also check for failures in any other network components to which the node is connected such as hubs, switches, or bridges.
```

Было внесено изменение в 8 мая 2018 г. до Windows Server 2016, которая была накопительное обновление для добавления устойчивых обрабатывает SMB для дисковых внутрикластерной сети SMB. Это было сделано для повышения эффективности устойчивость к временные неполадки в сети и как RoCE обрабатывает перегрузки сети. Эти улучшения также случайно увеличить время ожидания, при попытке повторного подключения подключения SMB и ожиданий для времени ожидания при перезапуске узла. Эти проблемы могут повлиять на систему, которая находится под нагрузкой. При внеплановых простоях приостанавливает операции ввода-ВЫВОДА до 60 секунд также наблюдались во время ожидания для подключений к времени ожидания системы. Чтобы устранить эту проблему, установите [18 октября 2018 г., накопительное обновление для Windows Server 2016](https://support.microsoft.com/help/4462928) или более поздней версии.

*Примечание* это обновление выравнивает CSV времени ожидания, время ожидания подключения SMB, чтобы устранить эту проблему. Он не реализует изменения, чтобы отключить создание дампа в реальном времени, упомянутых в соответствующем разделе.

### <a name="shutdown-process-flow"></a>Поток процесса завершения работы:

1. Выполните командлет Get-VirtualDisk и убедитесь, что значение HealthStatus — работоспособное состояние.
2. Выполнить сток узла, выполнив следующий командлет:

   ```powershell
   Suspend-ClusterNode -Drain
   ```
3. Поместите диски на этом узле в режиме обслуживания хранилища, выполнив следующий командлет: 

   ```powershell
   Get-StorageFaultDomain -type StorageScaleUnit | Where-Object {$_.FriendlyName -eq "<NodeName>"} | Enable-StorageMaintenanceMode
   ```
4. Запустите **Get-PhysicalDisk** командлета и убедитесь, что свойство operationalstatus имеет значение возвращается в режим обслуживания.
5. Запустите **Restart-Computer** командлет для перезапуска узла.
6. После перезагрузки узла Удалите диски на этом узле из режима обслуживания хранилища, выполнив следующий командлет:

   ```powershell
   Get-StorageFaultDomain -type StorageScaleUnit | Where-Object {$_.FriendlyName -eq "<NodeName>"} | Disable-StorageMaintenanceMode
   ```
7. Возобновить его работу, запустив следующий командлет:

   ```powershell
   Resume-ClusterNode
   ```
8. Проверьте состояние заданий повторной синхронизации, выполнив следующий командлет:

   ```powershell
   Get-StorageJob
   ```

### <a name="disabling-live-dumps"></a>Отключение динамической дампы
Чтобы устранить последствия создания дампа в реальном времени в системах, которые имеют большой объем памяти и под нагрузкой, кроме того может потребоваться отключить формирование дампа в реальном времени. Ниже приведены три варианта.

>[!Caution]
>Эту процедуру можно запретить сбор диагностических сведений, технической поддержки Майкрософт может потребоваться исследовать эту проблему. Представителю службы поддержки может потребоваться попросить вас для повторного включения создания дампа в реальном времени, на основе конкретных сценариев устранения неполадок.

Существует два метода для отключения динамической дампы памяти, как описано ниже.

#### <a name="method-1-recommended-in-this-scenario"></a>Метод 1 (рекомендуется в этом сценарии)
Чтобы полностью отключить все дампы памяти, включая динамические дампы всей системы, выполните следующие действия.

1. Создайте следующий раздел реестра: HKLM\System\CurrentControlSet\Control\CrashControl\ForceDumpsDisabled
2. В новом **ForceDumpsDisabled** ключа, создайте свойство REG_DWORD как GuardedHost и затем присвойте ему значение 0x10000000.
3. Примените новый ключ реестра на каждом узле кластера.

>[!NOTE]
>Необходимо перезагрузить компьютер nregistry чтобы изменения вступили в силу.

После этого раздела реестра установлен, динамического создания дампа не удастся и создает ошибку «STATUS_NOT_SUPPORTED».

#### <a name="method-2"></a>Метод 2
По умолчанию отчеты об ошибках Windows позволит только один LiveDump каждого типа отчета 7 дней и только 1 LiveDump на каждом компьютере за 5 дней. Можно изменить, задав следующие разделы реестра, разрешая только один LiveDump на компьютере неограниченно долго.
```
reg add "HKLM\Software\Microsoft\Windows\Windows Error Reporting\FullLiveKernelReports" /v SystemThrottleThreshold /t REG_DWORD /d 0xFFFFFFFF /f
```
```
reg add "HKLM\Software\Microsoft\Windows\Windows Error Reporting\FullLiveKernelReports" /v ComponentThrottleThreshold /t REG_DWORD /d 0xFFFFFFFF /f
```

*Примечание* необходимо перезагрузить компьютер, чтобы изменение вступило в силу.

### <a name="method-3"></a>Метод 3
Чтобы отключить создание кластера, динамической дампов (например, когда регистрируется событие 5120), выполните следующий командлет:

```powershell
(Get-Cluster).DumpPolicy = ((Get-Cluster).DumpPolicy -band 0xFFFFFFFFFFFFFFFE)
```
Этот командлет имеет вступает в силу на всех узлах кластера без перезагрузки компьютера.

## <a name="slow-io-performance"></a>Низкая производительность операций ввода-ВЫВОДА

Если вы видите низкой производительности операций ввода-ВЫВОДА, проверьте, включена ли кэш в конфигурации дисковых пространств. 

Чтобы проверить двумя способами: 


1. С помощью журнала кластера. Откройте журнал кластера в любом удобном текстовом редакторе и найдите «[==== диски SBL ====].» Это будет список на узле, который создан журнал на диск. 

     Кэш включен пример диски: Здесь, обратите внимание, что CacheDiskStateInitializedAndBound находится в состоянии, и это здесь присутствует GUID. 

   ```
   [=== SBL Disks ===]
    {26e2e40f-a243-1196-49e3-8522f987df76},3,false,true,1,48,{1ff348f1-d10d-7a1a-d781-4734f4440481},CacheDiskStateInitializedAndBound,1,8087,54,false,false,HGST    ,HUH721010AL4200 ,        7PG3N2ER,A21D,{d5e27a3b-42fb-410a-81c6-9d8cc12da20c},[R/M 0 R/U 0 R/T 0 W/M 0 W/U 0 W/T 0],
    ```

    Кэш не включен: Здесь мы видим, есть идентификатор GUID не существует и находится в состоянии CacheDiskStateNonHybrid. 
    ```
   [=== SBL Disks ===]
    {426f7f04-e975-fc9d-28fd-72a32f811b7d},12,false,true,1,24,{00000000-0000-0000-0000-000000000000},CacheDiskStateNonHybrid,0,0,0,false,false,HGST    ,HUH721010AL4200 ,        7PGXXG6C,A21D,{d5e27a3b-42fb-410a-81c6-9d8cc12da20c},[R/M 0 R/U 0 R/T 0 W/M 0 W/U 0 W/T 0],
    ```

    Кэш не включен: Когда все диски имеют тот же тип регистр не включена по умолчанию. Здесь мы видим, есть идентификатор GUID не существует и находится в состоянии CacheDiskStateIneligibleDataPartition. 
    ```
    {d543f90c-798b-d2fe-7f0a-cb226c77eeed},10,false,false,1,20,{00000000-0000-0000-0000-000000000000},CacheDiskStateIneligibleDataPartition,0,0,0,false,false,NVMe    ,INTEL SSDPE7KX02,  PHLF7330004V2P0LGN,0170,{79b4d631-976f-4c94-a783-df950389fd38},[R/M 0 R/U 0 R/T 0 W/M 0 W/U 0 W/T 0], 
    ```  
2. С помощью Get-PhysicalDisk.xml из SDDCDiagnosticInfo
    1. Open the XML file using "$d = Import-Clixml GetPhysicalDisk.XML"
    2. Запустите «ipmo хранилище»
    3. run "$d". Обратите внимание на то, что использование автоматический выбор, не журнала вы увидите примерно такой результат: 

   |FriendlyName|  SerialNumber| MediaType| CanPool| OperationalStatus| HealthStatus| Использование| Размер|
   |-----------|------------|---------| -------| -----------------| ------------| -----| ----|
   |NVMe INTEL SSDPE7KX02| PHLF733000372P0LGN| SSD| False|   ОК|                Работоспособное|      Автоматический выбор 1,82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF7504008J2P0LGN| SSD|  False|    ОК|                Работоспособное| Автовыбор| 1.82 ТБ|
   |NVMe INTEL SSDPE7KX02| PHLF7504005F2P0LGN| SSD|  False|  ОК|                Работоспособное| Автовыбор| 1.82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF7504002A2P0LGN| SSD| False| ОК|    Работоспособное| Автовыбор| 1.82 ТБ|
   |NVMe INTEL SSDPE7KX02| PHLF7504004T2P0LGN |SSD| False|ОК|       Работоспособное| Автовыбор| 1.82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF7504002E2P0LGN| SSD| False| ОК|      Работоспособное| Автовыбор| 1.82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF7330002Z2P0LGN| SSD| False| ОК|      Работоспособное|Автовыбор| 1.82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF733000272P0LGN |SSD| False| ОК|  Работоспособное| Автовыбор| 1.82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF7330001J2P0LGN |SSD| False| ОК| Работоспособное| Автовыбор| 1.82 ТБ|
   |NVMe INTEL SSDPE7KX02| PHLF733000302P0LGN |SSD| False| ОК|Работоспособное| Автовыбор| 1.82 ТБ|
   |NVMe INTEL SSDPE7KX02| PHLF7330004D2P0LGN |SSD| False| ОК| Работоспособное| Автовыбор |1.82 ТБ|

## <a name="how-to-destroy-an-existing-cluster-so-you-can-use-the-same-disks-again"></a>Как удалить кластер для использования тех же дисках

В кластере дисковыми пространствами, один раз отключить дисковых пространств и использовать процесс очистки, описанный в [очистке устройств](deploy-storage-spaces-direct.md#step-31-clean-drives), кластерного пула носителей по-прежнему остается в автономном режиме, и служба работоспособности будет удалено из кластер.

Следующим шагом является удаление пула носителей фантомов: 
   ```powershell
   Get-ClusterResource -Name "Cluster Pool 1" | Remove-ClusterResource
   ```

Теперь, если вы запустите **Get-PhysicalDisk** на любой из узлов, вы увидите все диски, которые были в пуле. Например в лаборатории с 4-узловой кластер с 4 дисками SAS, 100 ГБ для каждого узла. В этом случае после отключения пространства дисковыми которой удаляет SBL (уровня шины хранилища), но оставляет фильтра, в том случае, если вы запустите **Get-PhysicalDisk**, метод должен сообщить 4 диска, за исключением локального диска операционной системы. Вместо этого оно отмечено 16 вместо этого. Это то же самое для всех узлов в кластере. При запуске **Get-Disk** команды, вы увидите локально подключенные диски, нумеруются как 0, 1, 2 и т. д., как показано в этом примере выходных данных:

|Number| Понятное имя| Серийный номер|HealthStatus|OperationalStatus|Общий размер| Стиль раздела|
|-|-|-|-|-|-|-|-|
|0|MSFT виртуальной...  ||Работоспособное | Online|  127 ГБ| GPT|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
|1|MSFT виртуальной...||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
|2|MSFT виртуальной...||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
|4|MSFT виртуальной...||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
|3|MSFT виртуальной...||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||MSFT виртуальной... ||Работоспособное| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|


## <a name="error-message-about-unsupported-media-type-when-you-create-an-storage-spaces-direct-cluster-using-enable-clusters2d"></a>Сообщение об ошибке о «неподдерживаемый тип носителя» при создании кластер дисковых пространств, с помощью Enable-ClusterS2D  

Вы можете увидеть ошибки, аналогичную следующей, при запуске **Enable-ClusterS2D** командлета:

![Сообщение об ошибке сценарий 6](media/troubleshooting/scenario-error-message.png)

Чтобы устранить эту проблему, убедитесь, что адаптер HBA настроен режим адаптера ШИНЫ. Нет адаптеров ШИНЫ должен быть настроен в режиме RAID.  

## <a name="enable-clusterstoragespacesdirect-hangs-at-waiting-until-sbl-disks-are-surfaced-or-at-27"></a>Enable-ClusterStorageSpacesDirect зависает на «Ожидает, пока SBL диски отображаются» или на 27%

Вы увидите следующие сведения в отчете о проверке:

    Disk <identifier> connected to node <nodename> returned a SCSI Port Association and the corresponding enclosure device could not be found. The hardware is not compatible with Storage Spaces Direct (S2D), contact the hardware vendor to verify support for SCSI Enclosure Services (SES). 


Проблема заключается в том, с картой расширителя HPE SAS, которое находится между диски и адаптеру ШИНЫ. Расширитель SAS создает повторяющийся идентификатор между первый диск, подключенный к расширитель и сам расширителя.  Эта проблема была решена в [HPE смарт-массива контроллеров SAS расширитель встроенного по: 4.02](https://support.hpe.com/hpsc/swd/public/detail?sp4ts.oid=7304566&swItemId=MTX_ef8d0bf4006542e194854eea6a&swEnvOid=4184#tab3).

## <a name="intel-ssd-dc-p4600-series-has-a-non-unique-nguid"></a>Серия Intel SSD DC P4600 имеет неуникальное NGUID
Вы можете увидеть ошибку где похоже на устройство серии Intel SSD DC P4600 сообщать о подобных 16-байтовое NGUID для нескольких пространств имен, например 0100000001000000E4D25C000014E214 или 0100000001000000E4D25C0000EEE214 в следующем примере.


|               Уникальный идентификатор               | идентификатор устройства | MediaType | BusType |               серийный номер               |      size      | canpool | FriendlyName | OperationalStatus |
|--------------------------------------|----------|-----------|---------|------------------------------------------|----------------|---------|--------------|-------------------|
|           5000CCA251D12E30           |    0     |    Жесткий диск    |   SAS   |                 7PKR197G                 | 10000831348736 |  False  |     HGST     |  HUH721010AL4200  |
| eui.0100000001000000E4D25C000014E214 |    4     |    SSD    |  NVMe   | 0100_0000_0100_0000_E4D2_5C00_0014_E214. | 1600321314816  |  True   |    INTEL     |   SSDPE2KE016T7   |
| eui.0100000001000000E4D25C000014E214 |    5     |    SSD    |  NVMe   | 0100_0000_0100_0000_E4D2_5C00_0014_E214. | 1600321314816  |  True   |    INTEL     |   SSDPE2KE016T7   |
| EUI.0100000001000000E4D25C0000EEE214 |    6     |    SSD    |  NVMe   | 0100_0000_0100_0000_E4D2_5C00_00EE_E214. | 1600321314816  |  True   |    INTEL     |   SSDPE2KE016T7   |
| EUI.0100000001000000E4D25C0000EEE214 |    7     |    SSD    |  NVMe   | 0100_0000_0100_0000_E4D2_5C00_00EE_E214. | 1600321314816  |  True   |    INTEL     |   SSDPE2KE016T7   |

Чтобы устранить эту проблему, обновите встроенное по Intel диски до последней версии.  Версия встроенного по для устранения этой проблемы известен QDV101B1 от мая 2018 г.

[Мая 2018 версии Intel SSD Data Center средства](https://downloadmirror.intel.com/27778/eng/Intel_SSD_Data_Center_Tool_3_0_12_Release_Notes_330715-026.pdf) включает в себя обновление встроенного по, QDV101B1, серии Intel SSD DC P4600.


## <a name="physical-disk-healthy-and-operational-status-is-removing-from-pool"></a>Физический диск «Исправен» и рабочее состояние — «Удаление из пула» 

В кластере Windows Server 2016 Storage Spaces Direct может появиться HealthStatus для одной или нескольких физических дисков как «Исправен», хотя свойство operationalstatus имеет значение "(удаление из пула, ОК).» 

«Удаление из пула» объекта intent задается, если **Remove-PhysicalDisk** будет вызван, но хранятся в службе работоспособности для поддержания состояния и обеспечить возможность восстановления при сбое операции удаления. Можно вручную изменить свойство operationalstatus имеет значение Исправен с одним из следующих методов:

- Удалить физический диск из пула и затем снова добавьте его.
- Запустите [скрипт Clear-PhysicalDiskHealthData.ps1](https://go.microsoft.com/fwlink/?linkid=2034205) очистить цель. (Доступные для загрузки в формате. Txt-файл. Необходимо сохранить его как. Ps1-файл перед его выполнением.)

Ниже приведены некоторые примеры, в котором показано, как запустить сценарий.

- Используйте **SerialNumber** параметр для указания диска, необходимо задать в работоспособное состояние. Можно получить серийный номер от **WMI MSFT_PhysicalDisk** или **Get-PhysicalDIsk**. (Мы просто используем 0s для ниже серийный номер.)

   ```powershell
   Clear-PhysicalDiskHealthData -Intent -Policy -SerialNumber 000000000000000 -Verbose -Force
    ```

- Используйте **UniqueId** параметр для указания диска (из **WMI MSFT_PhysicalDisk** или **Get-PhysicalDIsk**).

   ```powershell
   Clear-PhysicalDiskHealthData -Intent -Policy -UniqueId 00000000000000000 -Verbose -Force
   ```

## <a name="file-copy-is-slow"></a>Копирование файлов работает медленно

Может отображаться проблеме с помощью проводника для копирования большого VHD к виртуальному диску — копирование файлов занимает больше времени чем ожидалось.

С помощью проводника, Robocopy или Xcopy для копирования большого VHD к виртуальному диску не рекомендуемый метод так как это вызовет медленнее, чем ожидаемая производительность. Процесс копирования не осуществляется с помощью дисковых пространств стек, который находится ниже в стеке хранилища, а вместо этого действует как процесс локальную копию.

Если вы хотите протестировать производительность дисковых пространств, мы рекомендуем использовать VMFleet и Diskspd для нагрузки и нагрузочное тестирование серверы для получения опорной линией и устанавливает ожидания производительности дисковых пространств.

## <a name="expected-events-that-you-would-see-on-rest-of-the-nodes-during-the-reboot-of-a-node"></a>Ожидается события, которые отображаются на остальных узлов во время перезагрузки узла. 

Его можно не учитывать эти события: 

    Event ID 205: Windows lost communication with physical disk {XXXXXXXXXXXXXXXXXXXX }. This can occur if a cable failed or was disconnected, or if the disk itself failed. 

    Event ID 203: Windows lost communication with physical disk {xxxxxxxxxxxxxxxxxxxxxxxx }. This can occur if a cable failed or was disconnected, or if the disk itself failed. 

Если вы используете виртуальные машины Azure, вы можете пропустить это событие:

    Event ID 32: The driver detected that the device \Device\Harddisk5\DR5 has its write cache enabled. Data corruption may occur. 

## <a name="slow-performance-or-lost-communication-io-error-detached-or-no-redundancy-errors-for-deployments-that-use-intel-p3x00-nvme-devices"></a>Низкая производительность или «Связь потеряна,» «Ошибка ввода-ВЫВОДА», «Отключен», или «Нет избыточности» ошибки для развертываний, использующих устройства Intel P3x00 NVMe

Мы определили критической ошибки, которая затрагивает некоторые дисковые пользователей, при использовании оборудования, на основе семейства Intel P3x00 действия NVM Express (NVMe) устройств с версиями встроенного по перед «Обслуживания выпуск 8». 

>[!NOTE]
> Отдельные изготовители оборудования могут иметь устройства, которые основаны на семейства Intel P3x00 NVMe устройств с помощью уникального встроенного по версии строк. Дополнительные сведения о последней версии встроенного по, обратитесь к изготовителю Оборудования.

При использовании оборудования в развертывании на основе Intel P3x00 семейства устройств NVMe, рекомендуется немедленно применить последние микропрограммы (по крайней мере 8 обслуживания выпуска). Это [статье службы поддержки Майкрософт](https://support.microsoft.com/help/4052341/slow-performance-or-lost-communication-io-error-detached-or-no-redunda) Дополнительные сведения об этой проблеме. 
