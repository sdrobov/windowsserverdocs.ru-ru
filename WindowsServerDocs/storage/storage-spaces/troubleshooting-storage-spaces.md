---
title: Устранение неполадок дисковые пространства хранилища
description: Узнайте, как устранять развертыванием локальных дисковых пространств.
keywords: Дисковые пространства
ms.prod: windows-server-threshold
ms.author: ''
ms.technology: storage-spaces
ms.topic: article
author: kaushika-msft
ms.date: 10/24/2018
ms.localizationpriority: medium
ms.openlocfilehash: c7c9573732ff1cf5a998588b1aec81915c227ee2
ms.sourcegitcommit: 5d55c3ebd1ceee7229ea9a9989c69cf93757ed88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2019
ms.locfileid: "9256937"
---
# Устранение неполадок локальных дисковых пространств

Используйте следующие сведения отладки развертывания локальных дисковых пространств.

Как правило начните, выполнив следующие действия:

1. Убедитесь, что Марка и модель SSD Сертифицировано для Windows Server 2016 с помощью каталог Windows Server. С помощью поставщика убедитесь, что диски поддерживают локальных дисковых пространств.
2. Проверьте хранилище для проблемным диски. Используйте программное обеспечение управления хранилища для проверки состояния дисков. Если диски являются проблемным, обратитесь к поставщику. 
3. Обновите хранилища и встроенного по диска при необходимости.
   Убедитесь, что установлены последние обновления Windows на всех узлах. Вы можете получить последние обновления для Windows Server 2016 от [https://aka.ms/update2016](https://aka.ms/update2016).
4. Обновить встроенное по и драйверы сетевого адаптера.
5. Запуск проверки кластеров и ознакомьтесь с разделом пространств места хранения, убедиться дисков, которые будут использоваться для кэша, отображаются правильно и без ошибок.

Если по-прежнему возникают проблемы, ознакомьтесь с описанными ниже сценариями.

## Ресурсы виртуального диска, в состоянии избыточность нет
Узлы локальные дисковые системы неожиданно перезапустите из-за аварийном завершении или сбое питания. Выберите один или несколько виртуальных жестких дисков может не перейдет в оперативный режим, после чего описание «избыточность недостаточно информации.»
    
|friendlyName|ResiliencySettingName| OperationalStatus| HealthStatus| IsManualAttach|Size| PSComputerName|
|------------|---------------------| -----------------| ------------| --------------|-----| --------------|
|Disk4| Отражение (Mirror)| ОК|  Healthy| True|  10 ТБ|  Узел 01.conto …|
|Disk3         |Отражение (Mirror)                 |ОК                          |Healthy       |True            |10 ТБ | Узел 01.conto …|
|Disk2         |Отражение (Mirror)                 |Без резервирования               |Unhealthy     |True            |10 ТБ | Узел 01.conto …|
|Диск 1         |Отражение (Mirror)                 |{Без резервирования, InService}  |Unhealthy     |True            |10 ТБ | Узел 01.conto …| 

Кроме того после попытки подключить виртуальный диск, следующие сведения регистрируется в журнале кластера (DiskRecoveryAction).  

```
[Verbose] 00002904.00001040::YYYY/MM/DD-12:03:44.891 INFO [RES] Physical Disk <DiskName>: OnlineThread: SuGetSpace returned 0.
[Verbose] 00002904.00001040:: YYYY/MM/DD -12:03:44.891 WARN [RES] Physical Disk < DiskName>: Underlying virtual disk is in 'no redundancy' state; its volume(s) may fail to mount.
[Verbose] 00002904.00001040:: YYYY/MM/DD -12:03:44.891 ERR [RES] Physical Disk <DiskName>: Failing online due to virtual disk in 'no redundancy' state. If you would like to attempt to online the disk anyway, first set this resource's private property 'DiskRecoveryAction' to 1. We will try to bring the disk online for recovery, but even if successful, its volume(s) or CSV may be unavailable. 
``` 

**Нет избыточности рабочее состояние** может произойти, если диск не удалось или если система не может получить доступ к данным на виртуальном диске. Эта проблема может произойти, если перезагрузка происходит на узле во время обслуживания на узлах.
    
Чтобы устранить эту проблему, выполните следующие действия.

1. Удалите затронутые виртуальных дисков из CSV-файла. Это поместить их в группе «Доступное хранилище» в кластере и начнут как типа ресурса из «Физический диск».

   ```powershell
   Remove-ClusterSharedVolume -name "VdiskName"
   ``` 
2. На узле, который является владельцем группы доступное хранилище, выполните следующую команду на каждый диск, который находится в состоянии избыточность нет. Для определения какой из узлов в группу «Доступное хранилище» включен вы можете выполните следующую команду.

   ```powershell
   Get-ClusterGroup
   ```
3. Задать действие по восстановлению диска, а затем запустите этих дисков.
   ```powershell
   Get-ClusterResource "VdiskName" | Set-ClusterParameter -Name DiskRecoveryAction -Value 1
   Start-ClusterResource -Name "VdiskName"
   ```
4. Восстановление должна запуститься автоматически. Подождите, пока для завершения процесса восстановления. Она может перейти в приостановленное состояние и запустить его снова. Отслеживать ход выполнения: 
    - Запустите **Get-StorageJob** отслеживать состояние восстановления и см. в разделе после его завершения.
    - Запустите **Get-VirtualDisk** и убедитесь, что пространство возвращает HealthStatus из работоспособна.
5. После восстановления по завершении и виртуальные диски, Исправен, изменение, которое параметров виртуального диска "Назад".

   ```powershell
    Get-ClusterResource "VdiskName" | Set-ClusterParameter -Name DiskRecoveryAction -Value 0
   ```
6. Предпринять диски, которые автономного и затем снова, чтобы у DiskRecoveryAction вступают в силу.

   ```powershell
   Stop-ClusterResource "VdiskName"
   Start-ClusterResource "VdiskName"
   ``` 
7. Добавьте затронутые виртуальных дисков обратно в формате CSV.

   ```powershell
   Add-ClusterSharedVolume -name "VdiskName"
   ```

**DiskRecoveryAction** — это коммутатор переопределения, позволяющий прикрепить объем пространства в режиме чтения и записи без каких-либо проверок. Свойство позволяет выполнять диагностики в почему тома не перейдет в оперативный режим. Это очень похож на режим обслуживания, но вы можете вызывать на ресурс в состоянии сбой. Он также позволяет получать доступ к данным, который может быть особенно удобны в ситуациях, таких как «Нет избыточности,» где можно получить доступ к любой данным можно и скопируйте его. Свойство DiskRecoveryAction был добавлен в 22 феврале 2018 г. обновление, 4077525 КБ.
    
    
## Отключенные состояния в кластере 

При выполнении командлета **Get-VirtualDisk** отсоединяется OperationalStatus для одного или нескольких локальных дисковых пространствах виртуальные диски. Тем не менее HealthStatus, о которых сообщил командлет **Get-PhysicalDisk** означает, что все физические диски в работоспособном состоянии.

Ниже приведен пример выходных данных командлета **Get-VirtualDisk** .

|friendlyName|  ResiliencySettingName|  OperationalStatus|   HealthStatus|  IsManualAttach|  Size|   PSComputerName|
|-|-|-|-|-|-|-|
|Disk4|         Отражение (Mirror)|                 ОК|                  Healthy|       True|            10 ТБ|  Узел 01.conto …|
|Disk3|         Отражение (Mirror)|                 ОК|                  Healthy|       True|            10 ТБ|  Узел 01.conto …|
|Disk2|         Отражение (Mirror)|                 Отключен|            Unknown (неизвестно).|       True|            10 ТБ|  Узел 01.conto …|
|Диск 1|         Отражение (Mirror)|                 Отключен|            Unknown (неизвестно).|       True|            10 ТБ|  Узел 01.conto …| 


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

**Отключенные рабочее состояние** может произойти, если неизменяемую область и отслеживания (DRT) журнал заполнен. Дисковые использует задать область отслеживания (DRT) для зеркального пространств убедитесь, что при возникновении сбоя питания, любой выполняемый обновления метаданные записываются в убедитесь, что дисковое пространство можно вернуть или отменить операции, чтобы вернуть дисковое пространство в гибкой и согласованность при восстановлении питания и система будет восстановлена. При переполнении журнала DRT виртуальный диск не удается подключить до синхронизации и очищены метаданные DRT. Для этого необходимо под управлением полную проверку, что может занять несколько часов.
    
Чтобы устранить эту проблему, выполните следующие действия.
1. Удалите затронутые виртуальных дисков из CSV-файла.

   ```powershell
   Remove-ClusterSharedVolume -name "VdiskName"
   ``` 
2. Выполните следующие команды на каждый диск, не возвращается в оперативный режим. 

   ```powershell
   Get-ClusterResource -Name "VdiskName" | Set-ClusterParameter DiskRunChkDsk 7
   Start-ClusterResource -Name "VdiskName"
   ``` 
3. Выполните следующую команду на каждом узле, в котором отключенные том подключен. 

   ```powershell
   Get-ScheduledTask -TaskName "Data Integrity Scan for Crash Recovery" | Start-ScheduledTask 
   ```
   Эта задача должен вызываться на всех узлах, на которых работает отключенные тома. Восстановление должна запуститься автоматически. Подождите, пока для завершения процесса восстановления. Она может перейти в приостановленное состояние и запустить его снова. Отслеживать ход выполнения: 
   - Запустите **Get-StorageJob** отслеживать состояние восстановления и см. в разделе после его завершения.
   -  Запустите **Get-VirtualDisk** и убедитесь, что пространство возвращает HealthStatus из работоспособна.
    - «Целостности проверки для сбой восстановления данных» является задачу, которая не отображается как задание хранилища, и нет не индикатор хода выполнения. Если задача отображается как запущенные, он запущен. Когда он завершает работу, он отобразит завершенных.
    
       Кроме того вы можете просмотреть состояние выполнение задачи расписание с помощью следующего командлета: 
       ```powershell
       Get-ScheduledTask | ? State -eq running
       ``` 
4. Сразу же после завершения «целостности проверки для сбой восстановления данных» завершения восстановления и виртуальные диски являются Исправен, изменение, которое параметров виртуального диска "Назад". 

   ```powershell
   Get-ClusterResource -Name "VdiskName" | Set-ClusterParameter DiskRunChkDsk 0 
   ```
5. Добавьте затронутые виртуальных дисков обратно в формате CSV.    

   ```powershell
   Add-ClusterSharedVolume -name "VdiskName"
   ```  
**DiskRunChkdsk значение 7** используется для присоединения пространства тома и иметь раздел в режиме только для чтения. Это позволяет дисковых самостоятельно обнаружения и self-heal посредством активации восстановления. Восстановление выполняется автоматически подключении. Он также позволяет получить доступ к данным, что может быть полезно для получения доступа к независимо от данных, вы можете скопировать. Для некоторых условий сбоя, например полный журнал DRT необходимо для выполнения проверки целостности данных для запланированной задачи сбой восстановления.
    
**Проверка целостности данных для восстановления сбой задачи** используется для синхронизации и очистить журнал полной задать область отслеживания (DRT). Эта задача может занять несколько часов. «Целостности проверки для сбой восстановления данных» является задачу, которая не отображается как задание хранилища, и нет не индикатор хода выполнения. Если задача отображается как запущенные, он запущен. Когда он завершает работу, он будет отображаться как завершенную. Если вы отмените задачу или перезапустите узел во время выполнения этой задачи, задача необходимо начать заново с самого начала.

Дополнительные сведения см. в разделе [по устранению неполадок локальных дисковых пространств работоспособности и рабочие состояния](storage-spaces-states.md).
    
## Событие 5120 с STATUS_IO_TIMEOUT c00000b5 

> [!Important]
> Чтобы уменьшить вероятность такая проблема при применении обновления с исправлением, рекомендуется использовать приведенную ниже процедуру режим обслуживания хранилища для установки [18 октября 2018 г., накопительное обновление для Windows Server 2016](https://support.microsoft.com/help/4462928) или более поздней версии При узлы уже установленной накопительного обновления Windows Server 2016, была выпущена из [8 мая 2018 г.](https://support.microsoft.com/help/4103723) в [9 октября 2018 г](https://support.microsoft.com/help/KB4462917).

Можно получить событие 5120 с STATUS_IO_TIMEOUT c00000b5 после перезагрузки узла в Windows Server 2016 с накопительным обновлением, которые выпускались из [может 8 КБ 2018 4103723](https://support.microsoft.com/help/4103723) [9 октября 2018 г. КБ 4462917](https://support.microsoft.com/help/4462917) установки.

При перезапуске узла 5120 событие регистрируется в журнале событий и включает один из следующих кодов ошибок:

```
Event Source: Microsoft-Windows-FailoverClustering
Event ID: 5120
Description:    Cluster Shared Volume 'CSVName' ('Cluster Virtual Disk (CSVName)') has entered a paused state because of 'STATUS_IO_TIMEOUT(c00000b5)'. All I/O will temporarily be queued until a path to the volume is reestablished. 

Cluster Shared Volume ‘CSVName’ ('Cluster Virtual Disk (CSVName)') has entered a paused state because of 'STATUS_CONNECTION_DISCONNECTED(c000020c)'. All I/O will temporarily be queued until a path to the volume is reestablished.    
```

При записи в журнал событий 5120 live дампа создается для сбора данных отладки, может привести к Дополнительные признаки или иметь влияние на производительность. Создание динамической дамп создает короткой паузы для включения снимка памяти будет записан файл дампа. Системы, которые имеют большой объем памяти и под нагрузкой может привести к узлам раскрываться членство в кластере и также привести к следующей 1135 событие в журнал.

```
Event source: Microsoft-Windows-FailoverClustering
Event ID: 1135  
Description: Cluster node 'NODENAME'was removed from the active failover cluster membership. The Cluster service on this node may have stopped. This could also be due to the node having lost communication with other active nodes in the failover cluster. Run the Validate a Configuration wizard to check your network configuration. If the condition persists, check for hardware or software errors related to the network adapters on this node. Also check for failures in any other network components to which the node is connected such as hubs, switches, or bridges.
```

Изменение был добавлен в 8 мая 2018 г. накопительное обновление для добавления устойчивыми обрабатывает SMB для локальных дисковых пространств сети SMB внутри кластера. Это было сделано для улучшения устойчивы к промежуточный сети и улучшения как RoCE обрабатывает перегрузки сети.

Эти улучшения также случайно увеличение времени ожидания при попытке подключения SMB подключить и ожидает время ожидания при перезапуске узла. Эти проблемы могут влиять на системах, которые под нагрузкой. Во время незапланированных простоев приостанавливает операций ввода-ВЫВОДА до 60 секунд также наблюдались пока система ожидает подключения к времени ожидания.

Чтобы устранить эту проблему, установите [18 октября 2018 г., накопительное обновление для Windows Server 2016](https://support.microsoft.com/help/4462928) или более поздней версии.

*Примечание* Это обновление переводит времени ожидания CSV-файла, время ожидания подключения SMB, чтобы устранить эту проблему. Он не реализует изменения для отключения поколения live дампа, упомянутых в разделе "решение".
    
### Завершение работы процессов:

1. Выполните командлет Get-VirtualDisk и убедитесь, что значение HealthStatus исправен.
2. Очистке узла, выполнив следующий командлет:

   ```powershell
   Suspend-ClusterNode -Drain
   ```
3. Поместите диски на этом узле в режиме обслуживания хранилища, выполнив следующий командлет: 

   ```powershell
   Get-StorageFaultDomain -type StorageScaleUnit | Where-Object {$_.FriendlyName -eq "<NodeName>"} | Enable-StorageMaintenanceMode
   ```
4. Выполните командлет **Get-PhysicalDisk** и убедитесь, что значение OperationalStatus входит в режим обслуживания.
5. Выполните командлет **Restart-Computer** для перезапуска узла.
6. После перезагрузки узла, удалите диски на этом узле режим обслуживания хранилища, запустив следующий командлет:

   ```powershell
   Get-StorageFaultDomain -type StorageScaleUnit | Where-Object {$_.FriendlyName -eq "<NodeName>"} | Disable-StorageMaintenanceMode
   ```
7. Возобновление работы узла, выполнив следующий командлет:

   ```powershell
   Resume-ClusterNode
   ```
8. Проверьте состояние заданий, выполнив следующий командлет:

   ```powershell
   Get-StorageJob
   ```

### Отключение живых дампов
Чтобы снизить влияние live дампа поколения в системах, которые имеют большой объем памяти и под нагрузкой, кроме того необходимо отключить создание динамической дампа. Ниже приведены три варианта.

>[!Caution]
>Эта процедура может предотвратить сбора диагностических сведений, которые службы поддержки Майкрософт может потребоваться изучить эту проблему. Агент службы поддержки может потребоваться вам потребуется повторно включить live дампа поколения в определенных сценариях устранения неполадок.

Существуют два метода для отключения динамической дампов, как описано ниже.

#### Метод 1 (рекомендуется в этом сценарии)
Чтобы полностью отключить все дампы, действительными дампов уровня системы, в том числе выполните следующие действия.

1. Создайте следующий раздел реестра: HKLM\System\CurrentControlSet\Control\CrashControl\ForceDumpsDisabled
2. Новый раздел **ForceDumpsDisabled** создайте свойство REG_DWORD как GuardedHost и затем установите для него значение 0x10000000.
3. Применение нового раздела реестра на каждом узле кластера.

>[!NOTE]
>Необходимо перезапустить компьютер nregistry чтобы изменения вступили в силу.

После этого раздела реестра установите, динамический создания дампа ошибкой и создает ошибку «STATUS_NOT_SUPPORTED».

#### Способ 2
По умолчанию отчеты об ошибках Windows позволит только один LiveDump каждого типа отчета на 7 дней и только один LiveDump на каждый компьютер на 5 дней. Можно изменить, установив следующие разделы реестра разрешить только один LiveDump на компьютере бесконечно.
```
reg add "HKLM\Software\Microsoft\Windows\Windows Error Reporting\FullLiveKernelReports" /v SystemThrottleThreshold /t REG_DWORD /d 0xFFFFFFFF /f
```
```
reg add "HKLM\Software\Microsoft\Windows\Windows Error Reporting\FullLiveKernelReports" /v ComponentThrottleThreshold /t REG_DWORD /d 0xFFFFFFFF /f
```

*Примечание* Необходимо перезапустить компьютер, чтобы изменения вступили в силу.

### Способ 3
Чтобы запретить создания кластера live дампов (например, если записывается событие 5120), выполните следующий командлет:

```powershell
(Get-Cluster).DumpPolicy = ((Get-Cluster).DumpPolicy -band 0xFFFFFFFFFFFFFFFE)
```
Этот командлет имеет вступает в силу немедленно на всех узлах кластера без перезагрузки компьютера.
    
## Снижение производительности операций ввода-ВЫВОДА

Если вы наблюдаете снижение производительности операций ввода-ВЫВОДА, проверьте, включен ли кэш в локальных дисковых пространств конфигурации. 

Существует два способа проверки: 
     
 
1. С помощью журнала кластера. Откройте журнал кластера в текстовом редакторе по выбору и выполните поиск «[=== дисков SBL ===].» Это будет список на узле, который был создан журнал на диске. 

     Пример дисков кэша включено: Обратите внимание, здесь, состояние CacheDiskStateInitializedAndBound и есть GUID здесь. 

   ```
   [=== SBL Disks ===]
    {26e2e40f-a243-1196-49e3-8522f987df76},3,false,true,1,48,{1ff348f1-d10d-7a1a-d781-4734f4440481},CacheDiskStateInitializedAndBound,1,8087,54,false,false,HGST    ,HUH721010AL4200 ,        7PG3N2ER,A21D,{d5e27a3b-42fb-410a-81c6-9d8cc12da20c},[R/M 0 R/U 0 R/T 0 W/M 0 W/U 0 W/T 0],
    ```

    Кэш не включено: Здесь мы видим, нет нет GUID и состояние — CacheDiskStateNonHybrid. 
    ```
   [=== SBL Disks ===]
    {426f7f04-e975-fc9d-28fd-72a32f811b7d},12,false,true,1,24,{00000000-0000-0000-0000-000000000000},CacheDiskStateNonHybrid,0,0,0,false,false,HGST    ,HUH721010AL4200 ,        7PGXXG6C,A21D,{d5e27a3b-42fb-410a-81c6-9d8cc12da20c},[R/M 0 R/U 0 R/T 0 W/M 0 W/U 0 W/T 0],
    ```

    Кэш не включено: Если все диски являются того же типа регистр не включена по умолчанию. Здесь мы видим нет нет GUID и состояние — CacheDiskStateIneligibleDataPartition. 
    ```
    {d543f90c-798b-d2fe-7f0a-cb226c77eeed},10,false,false,1,20,{00000000-0000-0000-0000-000000000000},CacheDiskStateIneligibleDataPartition,0,0,0,false,false,NVMe    ,INTEL SSDPE7KX02,  PHLF7330004V2P0LGN,0170,{79b4d631-976f-4c94-a783-df950389fd38},[R/M 0 R/U 0 R/T 0 W/M 0 W/U 0 W/T 0], 
    ```  
2. С помощью Get-PhysicalDisk.xml из SDDCDiagnosticInfo
    1. Откройте XML-файл с помощью «$d = GetPhysicalDisk.XML Clixml импорта»
    2. Запустите «ipmo хранилища»
    3. Запустите «$d». Обратите внимание, что использование Автовыбор, не журнала вы увидите вывода следующим образом: 

   |friendlyName|  SerialNumber| MediaType| CanPool| OperationalStatus| HealthStatus| Использование| Size|
   |-----------|------------|---------| -------| -----------------| ------------| -----| ----|
   |NVMe INTEL SSDPE7KX02| PHLF733000372P0LGN| SSD| False|   ОК|                Healthy|      Автоматический выбор 1,82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF7504008J2P0LGN| SSD|  False|    ОК|                Healthy| Автоматический выбор| 1,82 ТБ|
   |NVMe INTEL SSDPE7KX02| PHLF7504005F2P0LGN| SSD|  False|  ОК|                Healthy| Автоматический выбор| 1,82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF7504002A2P0LGN| SSD| False| ОК|    Healthy| Автоматический выбор| 1,82 ТБ|
   |NVMe INTEL SSDPE7KX02| PHLF7504004T2P0LGN |SSD| False|ОК|       Healthy| Автоматический выбор| 1,82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF7504002E2P0LGN| SSD| False| ОК|      Healthy| Автоматический выбор| 1,82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF7330002Z2P0LGN| SSD| False| ОК|      Healthy|Автоматический выбор| 1,82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF733000272P0LGN |SSD| False| ОК|  Healthy| Автоматический выбор| 1,82 ТБ|
   |NVMe INTEL SSDPE7KX02 |PHLF7330001J2P0LGN |SSD| False| ОК| Healthy| Автоматический выбор| 1,82 ТБ|
   |NVMe INTEL SSDPE7KX02| PHLF733000302P0LGN |SSD| False| ОК|Healthy| Автоматический выбор| 1,82 ТБ|
   |NVMe INTEL SSDPE7KX02| PHLF7330004D2P0LGN |SSD| False| ОК| Healthy| Автоматический выбор |1,82 ТБ|
    
## Как уничтожить существующий кластер, поэтому вы можете использовать одинаковые диски снова

В кластере локальных дисковых пространств после отключения локальных дисковых пространств и использовать процесс очистки, описанный в [чистой диски](deploy-storage-spaces-direct.md#step-31-clean-drives), кластерные пуле остается в автономном режиме, и служба работоспособности удаляется из кластера.

Следующий шаг — удалить фиктивные пуле: 
   ```powershell
   Get-ClusterResource -Name "Cluster Pool 1" | Remove-ClusterResource
   ```

Теперь при выполнении **Get-PhysicalDisk** на узле, вы увидите все диски, которые были в пуле. Например в лаборатории с 4-кластер с узлами с 4 дисков SAS, 100 ГБ для каждого узла. В этом случае после прямой места хранения отключен, который удаляет SBL (уровня шины хранилища), но оставляет фильтра, при выполнении **Get-PhysicalDisk**, он должен сообщать 4 дисков, за исключением локального диска операционной системы. Вместо этого он передается 16 вместо. Это то же самое для всех узлов в кластере. При выполнении команды **Get-Disk** , вы увидите локально подключенных дисках нумеруются как 0, 1, 2 и т. д, как показано в этом примере выходных данных:

|Число| Понятное имя| Серийный номер|HealthStatus|OperationalStatus|Общий размер| Стиль раздела|
|-|-|-|-|-|-|-|-|
|0|Виртуальной MSFT …  ||Healthy | Online|  127 ГБ| GPT|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
|1|Виртуальной MSFT …||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
|2|Виртуальной MSFT …||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
|4|Виртуальной MSFT …||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
|3|Виртуальной MSFT …||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|
||Виртуальной MSFT … ||Healthy| Вне сети| 100 ГБ| НЕОБРАБОТАННЫЕ|

    
## Сообщение об ошибке о «тип неподдерживаемые мультимедиа» при создании кластера локальных дисковых пространств с помощью Enable-ClusterS2D  

При выполнении командлета **Enable-ClusterS2D** обнаружить ошибки, примерно так:

![Сообщение об ошибке сценарий 6](media/troubleshooting/scenario-error-message.png)

Чтобы устранить эту проблему, убедитесь, что HBA адаптер настроен в режиме HBA. Не HBA должен быть настроен в режиме RAID.  
    
## Enable-ClusterStorageSpacesDirect зависает на «Ожидание до SBL дисков доступны» или на 27%

Вы увидите в отчет о проверке следующие сведения:

    Disk <identifier> connected to node <nodename> returned a SCSI Port Association and the corresponding enclosure device could not be found. The hardware is not compatible with Storage Spaces Direct (S2D), contact the hardware vendor to verify support for SCSI Enclosure Services (SES). 
    
  
Проблема связана с картой расширителем HPE SAS, находится между диски и карты HBA. Расширителем SAS создает повторяющийся идентификатор между первый диск, подключенный к разворачивания и расширителем сам.  Эта проблема была решена в [HPE смарт-массив контроллеров SAS разворачивания встроенное по: 4.02](https://support.hpe.com/hpsc/swd/public/detail?sp4ts.oid=7304566&swItemId=MTX_ef8d0bf4006542e194854eea6a&swEnvOid=4184#tab3).
    
## Серия Intel SSD DC P4600 имеет неуникальные NGUID
Вы можете столкнуться проблема где устройство серии Intel SSD DC P4600 кажется, что будет передавать данные аналогично 16-байтового NGUID для нескольких пространств имен, например 0100000001000000E4D25C000014E214 или 0100000001000000E4D25C0000EEE214 в примере ниже.

|Уникальный идентификатор| DeviceID |MediaType| BusType| серийный номер| size|canpool| FriendlyName| OperationalStatus|
|-|-|-|-|-|-|-|-|-
|5000CCA251D12E30| 0| Жесткий диск| SAS| 7PKR197G|                  10000831348736 |False|HGST| HUH721010AL4200| ОК|
|EUI.0100000001000000E4D25C000014E214 |4|SSD| NVMe|   0100_0000_0100_0000_E4D2_5C00_0014_E214.|1600321314816|True| INTEL| SSDPE2KE016T7|  ОК|
|EUI.0100000001000000E4D25C000014E214 |5|        SSD|       NVMe|    0100_0000_0100_0000_E4D2_5C00_0014_E214.|  1600321314816|    True| INTEL| SSDPE2KE016T7|  ОК|
|EUI.0100000001000000E4D25C0000EEE214| 6|        SSD|       NVMe|    0100_0000_0100_0000_E4D2_5C00_00EE_E214.|  1600321314816|    True| INTEL| SSDPE2KE016T7|  ОК|
|EUI.0100000001000000E4D25C0000EEE214| 7|        SSD|       NVMe|    0100_0000_0100_0000_E4D2_5C00_00EE_E214.|  1600321314816|    True| INTEL| SSDPE2KE016T7|  ОК|

Чтобы устранить эту проблему, обновите встроенное по Intel диски до последней версии.  Версия микропрограммного обеспечения известно QDV101B1 с мая 2018 г. Чтобы решить эту проблему.

[Мая выпуска средство Intel SSD данных центра](https://downloadmirror.intel.com/27778/eng/Intel_SSD_Data_Center_Tool_3_0_12_Release_Notes_330715-026.pdf) включает в себя обновления встроенного по, QDV101B1, серии Intel SSD DC P4600.

    
## Физический диск «Исправен» и состояние операции — «Удалить из пула» 

В кластере Windows Server 2016 дисковые обнаружить HealthStatus для одну или несколько физических дисков как «Правильными», во время OperationalStatus «(удаление из пула, ОК).» 

«Удалить из пула» намерения задается, если **Remove-PhysicalDisk** будет вызван, но в работоспособности для отслеживания состояния и обеспечить возможность восстановления при сбое операции удаления. Вы можете вручную изменить OperationalStatus Исправен с одним из следующих методов:

- Удалить физический диск из пула, а затем добавьте его снова.
- Запустите [сценарий Clear PhysicalDiskHealthData.ps1](https://go.microsoft.com/fwlink/?linkid=2034205) для очистки намерение. (Доступны для скачивания как. Файл TXT. Вам потребуется сохранить его в качестве. Ps1 файл, прежде чем вы можете использовать ее.)

Ниже приведено несколько примеров, демонстрирующий запуск сценария:

- Используйте параметр **SerialNumber** указать диск, который необходимо задать исправен. Вы можете получить серийный номер из **WMI MSFT_PhysicalDisk** или **Get-PhysicalDIsk**. (Мы просто используем атаками для ниже серийный номер.)
   
   ```powershell
   Clear-PhysicalDiskHealthData -Intent -Policy -SerialNumber 000000000000000 -Verbose -Force
    ```

- Используйте параметр **Уникальный идентификатор** для указания на диске (еще раз в **WMI MSFT_PhysicalDisk** или **Get-PhysicalDIsk**).

   ```powershell
   Clear-PhysicalDiskHealthData -Intent -Policy -UniqueId 00000000000000000 -Verbose -Force
   ```

## Скопируйте файл работает медленно

Представить проблемы с помощью проводника для копирования большого виртуального жесткого диска на виртуальный диск — копия файла занимает больше времени, чем ожидалось.

С помощью проводника, Robocopy или Xcopy для копирования большого виртуального жесткого диска на виртуальный диск, который не рекомендуемый метод как это приведет к медленнее, чем ожидаемую производительность. Процесс копирования не проходят стека локальных дисковых пространств, который нижний размещается в стеке хранилища, а вместо этого выступает в качестве локальной копии процесса.

Если вы хотите протестировать локальных дисковых пространств производительность, мы рекомендуем использовать VMFleet и Diskspd для загрузки и нагрузочного тестирования серверы для получения основу и ожидания производительности локальных дисковых пространств.

## Предполагается, что события, которые вы бы смотрели на остальные узлы во время перезагрузки узла. 

Это можно игнорировать эти события: 

    Event ID 205: Windows lost communication with physical disk {XXXXXXXXXXXXXXXXXXXX }. This can occur if a cable failed or was disconnected, or if the disk itself failed. 

    Event ID 203: Windows lost communication with physical disk {xxxxxxxxxxxxxxxxxxxxxxxx }. This can occur if a cable failed or was disconnected, or if the disk itself failed. 

Если вы используете виртуальных машинах Azure, вы можете проигнорировать этого события:

    Event ID 32: The driver detected that the device \Device\Harddisk5\DR5 has its write cache enabled. Data corruption may occur. 
    
## Снижение производительности или «Утеряна,» «Ошибка ввода-ВЫВОДА», «Отключен», или «Нет избыточность» ошибок для развертываний с использованием устройств Intel P3x00 NVMe

Мы определили критична, влияет на некоторые локальных дисковых пространств пользователей, использующих оборудования на основе семейства Intel P3x00 NVM Express (NVMe) устройств с помощью версии встроенного по до «Обслуживание выпуска 8». 

>[!NOTE]
> Отдельные изготовители оборудования может иметь устройств, основанные на Intel P3x00 семейства устройств NVMe со строками уникальное встроенное по версии. Свяжитесь с изготовителем компьютера для получения дополнительных сведений последняя версия встроенного по.

Если вы используете оборудования при развертывании на основе Intel P3x00 семейства устройств NVMe, рекомендуется немедленно применить последние доступные встроенного по (по крайней мере обслуживания выпуска 8). Дополнительные сведения об этой проблеме в этой [статье службы поддержки Майкрософт](https://support.microsoft.com/en-us/help/4052341/slow-performance-or-lost-communication-io-error-detached-or-no-redunda) . 
