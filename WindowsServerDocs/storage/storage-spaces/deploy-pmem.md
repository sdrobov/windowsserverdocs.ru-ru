---
title: Понять и развернуть постоянной памяти
description: Подробные сведения о какие постоянной памяти и как настроить проверку подлинности с помощью дисковых пространств в Windows Server 2019 прямой.
keywords: Дисковыми пространствами, постоянной памяти, pmem, хранение, S2D
ms.assetid: ''
ms.prod: ''
ms.author: adagashe
ms.technology: storage-spaces
ms.topic: article
author: adagashe
ms.date: 3/26/2019
ms.localizationpriority: ''
ms.openlocfilehash: ed4b2669ad35a2ce0f818c65f7024ce905d9e4d6
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280047"
---
---
# <a name="understand-and-deploy-persistent-memory"></a>Понять и развернуть постоянной памяти

>Относится к: Windows Server 2019

Постоянной памяти (или PMem) — это новый тип технологии памяти, которая предоставляет уникальное сочетание по доступной цене большой емкости и сохраняемость. В этом разделе приводятся основные сведения о PMem и шаги, чтобы развернуть его с помощью 2019 Windows Server с дисковыми пространствами.

## <a name="background"></a>Фон

PMem является типом из долговременного DRAM (NVDIMM), скорость DRAM, но сохраняет его содержимого памяти с помощью циклов power (содержимое памяти остаются даже в том случае, если система выходит из строя в случае неожиданной потери мощности, инициированного пользователем завершения работы, сбоя системы т. д.). По этой причине выхода из места выполняется значительно быстрее, так как содержимое оперативной памяти не требуется перезагрузка. Другой уникальных характеристик является PMem байтов адресуемый, это означает, что вы также можно использовать как хранилище (именно слышите PMem называется память класса хранилища).


Чтобы узнать о некоторых из этих преимуществ, давайте взглянем на этой демонстрации от Microsoft Ignite 2018:

[![Демонстрация Pmem 2018 г. Microsoft Ignite](http://img.youtube.com/vi/8WMXkMLJORc/0.jpg)](http://www.youtube.com/watch?v=8WMXkMLJORc)

Любой системе хранения, которая обеспечивает отказоустойчивость обязательно делает распределенной копии записей, которые должен проходить через сети и влечет за собой усиления записи серверной части. По этой причине абсолютные наибольшего значения тест производительности операций ввода-ВЫВОДА обычно обеспечивается с помощью операций чтения, особенно в том случае, если система хранения должна очевидных оптимизации для чтения из локальной копии, когда это возможно, какой Storage Spaces Direct.

**Благодаря 100% операций чтения кластер обеспечивает 13,798,674 операций ввода-ВЫВОДА.**

![Снимок экрана 13.7m операций ввода-ВЫВОДА записей](media/deploy-pmem/iops-record.png)

Если вы внимательно посмотреть видео, можно заметить, в thatwhat больше сногсшибательной — задержка: хотя бы на более чем 13.7 операций ввода-ВЫВОДА M, файловой системы в Windows сообщает задержки, не всегда меньше 40 мкс! (Это символ для микросекунды, одно миллионного доли секунды). Это на порядок быстрее, чем что типичный поставщиков флэш-памяти гордостью объявления уже сегодня.

Вместе дисковых пространств в Windows Server 2019 и Intel® Optane™ DC постоянной памяти обеспечивает высочайшую производительность. Это ведущее в отрасли HCI тест производительности из более чем 13.7M операций ввода-ВЫВОДА, с прогнозируемым и очень низкой задержкой, является более чем в два раза наших предыдущих ведущими в отрасли эталона 6.7M операций ввода-ВЫВОДА. Что такое дополнительные, это время необходимо всего 12 узлами кластера, 25% меньше, чем два года назад.

![Увеличение операций ввода-ВЫВОДА](media/deploy-pmem/iops-gains.png)

Оборудование, используемое был 12-сервер кластера с помощью трехстороннее зеркальное отображение и с разделителями тома ReFS, **12** x Intel® S2600WFT, **384 Гиб** памяти, 2 x 28-core «CascadeLake» **1,5 ТБ**Intel® Optane™ DC постоянной памяти как кэш, **32 ТБ** NVMe (4 x 8 P4510 TB Intel® контроллера домена), как объем, **2** x Гбит/с 25 Mellanox ConnectX-4

В таблице ниже приведены показатели полной производительности: 

| Тест производительности                   | Производительность         |
|-----------------------------|---------------------|
| 4K 100% случайных операций чтения         | 13.8 миллиона операций ввода-ВЫВОДА   |
| 4 K 90/10, %, произвольного чтения или записи | 9.45 миллиона операций ввода-ВЫВОДА   |
| Последовательное чтение 2 МБ         | Пропускная способность 549 ГБИТ/с |

### <a name="supported-hardware"></a>Поддерживаемое оборудование

В следующей таблице показано поддерживаемых постоянной памяти оборудование для Windows Server 2019 и Windows Server 2016. Обратите внимание на то, что Intel Optane специально поддерживает режим памяти и режим direct приложения. Windows Server 2019 поддерживает операции смешанного режима.

| Технология постоянной памяти                                      | Windows Server 2016 | Windows Server 2019 |
|-------------------------------------------------------------------|--------------------------|--------------------------|
| **NVDIMM-N** в режиме Direct приложения                                       | Поддерживается                | Поддерживается                |
| **Intel Optane™ DC постоянной памяти** в режиме Direct приложения             | Не поддерживается            | Поддерживается                |
| **Intel Optane™ DC постоянной памяти** в режиме два уровня памяти (2LM) | Не поддерживается            | Поддерживается                |

Теперь рассмотрим, как настроить постоянной памяти.

## <a name="interleave-sets"></a>Interleave наборов

### <a name="understanding-interleave-sets"></a>Основные сведения о interleave наборов

Помните, что NVDIMM-N находится в стандартное гнездо модуля памяти DIMM (памяти), размещая данные ближе к процессору (таким образом, сокращая задержку и получение более высокую производительность). Чтобы создать на это, набор interleave при двух или более NVDIMMs Создание N-сторонним чередовании для обеспечения чередуются операции чтения и записи для увеличения пропускной способности. Наиболее распространенные настройки являются способом 2 или 4-процессорном чередование.

Чередующиеся наборы часто могут создаваться в BIOS платформах, чтобы сделать несколько устройств постоянной памяти отображаются в виде одного логического диска в Windows Server. Каждый логический диск в постоянной памяти содержит чередующийся набор физических устройств, выполнив:

```PowerShell
Get-PmemDisk
```

Ниже приведен пример вывода:

```
DiskNumber Size   HealthStatus AtomicityType CanBeRemoved PhysicalDeviceIds UnsafeShutdownCount
---------- ----   ------------ ------------- ------------ ----------------- -------------------
2          252 GB Healthy      None          True         {20, 120}         0
3          252 GB Healthy      None          True         {1020, 1120}      0
```

Мы видим, что диск логических pmem #2 содержит физические устройства Id20 и Id120 и pmem логический диск #3 содержит физические устройства Id1020 и Id1120. Мы может также веб-канал диска конкретных pmem Get-PmemPhysicalDevice для получения всех его физических NVDIMMs в interleave задать, как показано ниже.


```PowerShell
(Get-PmemDisk)[0] | Get-PmemPhysicalDevice
```

Ниже приведен пример вывода:

```
DeviceId DeviceType           HealthStatus OperationalStatus PhysicalLocation FirmwareRevision Persistent memory size Volatile memory size
-------- ----------           ------------ ----------------- ---------------- ---------------- ---------------------- --------------------
20       Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_C1     102005310        126 GB                 0 GB
120      Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_F1     102005310        126 GB                 0 GB
```

### <a name="configuring-interleave-sets"></a>Настройка наборов с чередованием

Чтобы настроить группу interleave, выполните следующий командлет PowerShell:

```PowerShell
Get-PmemUnusedRegion

RegionId TotalSizeInBytes DeviceId
-------- ---------------- --------
       1     270582939648 {20, 120}
       3     270582939648 {1020, 1120}
```

Это показывает все регионы постоянной памяти, не назначен диском логической постоянной памяти в системе.

Чтобы просмотреть все сведения устройства постоянной памяти в системе, включая тип устройства, расположения, работоспособности и рабочее состояние, т. д. можно выполните следующий командлет на локальном сервере:

```PowerShell
Get-PmemPhysicalDevice

DeviceId DeviceType           HealthStatus OperationalStatus PhysicalLocation FirmwareRevision Persistent memory size Volatile
                                                                                                                      memory size
-------- ----------           ------------ ----------------- ---------------- ---------------- ---------------------- --------------
1020     Intel INVDIMM device Healthy      {Ok}              CPU2_DIMM_C1     102005310        126 GB                 0 GB
1120     Intel INVDIMM device Healthy      {Ok}              CPU2_DIMM_F1     102005310        126 GB                 0 GB
120      Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_F1     102005310        126 GB                 0 GB
20       Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_C1     102005310        126 GB                 0 GB
```

Поскольку у нас есть доступные неиспользуемые pmem регион, мы можем создать новые диски постоянной памяти. Мы можем создать нескольких дисков постоянной памяти, с помощью неиспользуемых областей по:

```PowerShell
Get-PmemUnusedRegion | New-PmemDisk
Creating new persistent memory disk. This may take a few moments.
```

Озже, это можно сделать, мы просмотреть результаты, выполните команду:

```PowerShell
Get-PmemDisk

DiskNumber Size   HealthStatus AtomicityType CanBeRemoved PhysicalDeviceIds UnsafeShutdownCount
---------- ----   ------------ ------------- ------------ ----------------- -------------------
2          252 GB Healthy      None          True         {20, 120}         0
3          252 GB Healthy      None          True         {1020, 1120}      0
```

Следует отметить, что мы выполнения **Get-PhysicalDisk | Где MediaType - Eq SCM** вместо **Get-PmemDisk** для получения тех же результатов. Только что созданный постоянной памяти диска соответствует 1:1 для дисков, которые отображаются в PowerShell и Windows Admin Center.

### <a name="using-persistent-memory-for-cache-or-capacity"></a>С помощью постоянной памяти для кэша, либо емкости

Дисковые пространства в Windows Server 2019 поддерживает постоянные память используется в качестве кэша или емкости диска. См. в разделе, это [документации](understand-the-cache.md) Дополнительные сведения о настройке кэша и емкости дисков.

## <a name="creating-a-dax-volume"></a>При создании тома DAX

### <a name="understanding-dax"></a>Основные сведения о DAX

Существует два способа для доступа к постоянной памяти. Подробные сведения.

1. **Прямой доступ (DAX)** , который работает как память, чтобы получить минимальную задержку. Приложение непосредственно изменяет постоянной памяти, обходя стек. Обратите внимание на то, что это может использоваться только в файловой системе NTFS.
2. **Блокировать доступ**, который работает как хранилище для обеспечения совместимости приложений. Процесс передачи данных через стек в этой программе установки, и он может использоваться с NTFS и ReFS.

Пример этого можно увидеть ниже:

![Стек DAX](media/deploy-pmem/dax.png)

### <a name="configuring-dax"></a>Настройка DAX

Нам потребуется использовать командлеты PowerShell для создания тома DAX в постоянной памяти. С помощью **- IsDax** коммутатора, мы форматирование тома следует включить DAX.

```PowerShell
Format-Volume -IsDax:$true
```

В следующем фрагменте кода поможет вам создать DAX том на диске постоянной памяти.

```PowerShell
# Here we use the first pmem disk to create the volume as an example
$disk = (Get-PmemDisk)[0] | Get-PhysicalDisk | Get-Disk
# Initialize the disk to GPT if it is not initialized
If ($disk.partitionstyle -eq "RAW") {$disk | Initialize-Disk -PartitionStyle GPT}
# Create a partition with drive letter 'S' (can use any available drive letter)
$disk | New-Partition -DriveLetter S -UseMaximumSize


   DiskPath: \\?\scmld#ven_8980&dev_097a&subsys_89804151&rev_0018#3&1b1819f6&0&03018089fb63494db728d8418b3cbbf549997891#{53f56307-b6
bf-11d0-94f2-00a0c91efb8b}

PartitionNumber  DriveLetter Offset                                               Size Type
---------------  ----------- ------                                               ---- ----
2                S           16777216                                        251.98 GB Basic

# Format the volume with drive letter 'S' to DAX Volume
Format-Volume -FileSystem NTFS -IsDax:$true -DriveLetter S

DriveLetter FriendlyName FileSystemType DriveType HealthStatus OperationalStatus SizeRemaining      Size
----------- ------------ -------------- --------- ------------ ----------------- -------------      ----
S                        NTFS           Fixed     Healthy      OK                    251.91 GB 251.98 GB

# Verify the volume is DAX enabled
Get-Partition -DriveLetter S | fl


UniqueId             : {00000000-0000-0000-0000-000100000000}SCMLD\VEN_8980&DEV_097A&SUBSYS_89804151&REV_0018\3&1B1819F6&0&03018089F
                       B63494DB728D8418B3CBBF549997891:WIN-8KGI228ULGA
AccessPaths          : {S:\, \\?\Volume{cf468ffa-ae17-4139-a575-717547d4df09}\}
DiskNumber           : 2
DiskPath             : \\?\scmld#ven_8980&dev_097a&subsys_89804151&rev_0018#3&1b1819f6&0&03018089fb63494db728d8418b3cbbf549997891#{5
                       3f56307-b6bf-11d0-94f2-00a0c91efb8b}
DriveLetter          : S
Guid                 : {cf468ffa-ae17-4139-a575-717547d4df09}
IsActive             : False
IsBoot               : False
IsHidden             : False
IsOffline            : False
IsReadOnly           : False
IsShadowCopy         : False
IsDAX                : True                   # <- True: DAX enabled
IsSystem             : False
NoDefaultDriveLetter : False
Offset               : 16777216
OperationalStatus    : Online
PartitionNumber      : 2
Size                 : 251.98 GB
Type                 : Basic
```

## <a name="monitoring-health"></a>Мониторинг работоспособности

При использовании постоянной памяти, существует ряд различий в процесс мониторинга:

1. Энергонезависимую память не создает счетчики производительности, поэтому вы не увидите, если отображаются на диаграммах в Windows Admin Center физического диска.
2. Постоянной памяти не создает данных Storport 505, поэтому вы не будете получать выбросов упреждающего обнаружения.

Кроме того, процесс мониторинга совпадает со значением физического диска. Вы можете запрашивать работоспособность диска постоянной памяти, выполнив:

```PowerShell
Get-PmemDisk

DiskNumber Size   HealthStatus AtomicityType CanBeRemoved PhysicalDeviceIds UnsafeShutdownCount
---------- ----   ------------ ------------- ------------ ----------------- -------------------
2          252 GB Unhealthy    None          True         {20, 120}         2
3          252 GB Healthy      None          True         {1020, 1120}      0

Get-PmemDisk | Get-PhysicalDisk | select SerialNumber, HealthStatus, OperationalStatus, OperationalDetails

SerialNumber               HealthStatus OperationalStatus  OperationalDetails
------------               ------------ ------------------ ------------------
802c-01-1602-117cb5fc      Healthy      OK
802c-01-1602-117cb64f      Warning      Predictive Failure {Threshold Exceeded,NVDIMM_N Error}
```

**HealthStatus** показывает, является ли диск постоянной памяти работоспособным. **UnsafeshutdownCount** отслеживает количество остановок работы, которые могут привести к потере данных, с этим логическим диском. Это сумма счетчики небезопасный завершения работы всех базовых устройств постоянной памяти этого диска. Можно также использовать команды ниже, чтобы сведения о работоспособности для запроса. **OperationalStatus** и **OperationalDetails** предоставляют дополнительные сведения о состоянии работоспособности.

Запрос работоспособности постоянной памяти устройства:

```PowerShell
Get-PmemPhysicalDevice

DeviceId DeviceType           HealthStatus OperationalStatus PhysicalLocation FirmwareRevision Persistent memory size Volatile memory size
-------- ----------           ------------ ----------------- ---------------- ---------------- ---------------------- --------------------
1020     Intel INVDIMM device Healthy      {Ok}              CPU2_DIMM_C1     102005310        126 GB                 0 GB
1120     Intel INVDIMM device Healthy      {Ok}              CPU2_DIMM_F1     102005310        126 GB                 0 GB
120      Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_F1     102005310        126 GB                 0 GB
20       Intel INVDIMM device Unhealthy    {HardwareError}   CPU1_DIMM_C1     102005310        126 GB                 0 GB
```

Это показывает, какое устройство постоянной памяти находится в неработоспособном состоянии. Неработоспособные устройства (**DeviceId**) 20 соответствует варианта в приведенном выше примере. **PhysicalLocation** от BIOS может помочь определить, какие постоянной памяти устройство находится в неисправном состоянии.

## <a name="replacing-persistent-memory"></a>Замена постоянной памяти

Выше показано, как просмотреть состояние работоспособности в постоянной памяти. Если вам нужно заменить неисправный модуль, необходимо будет повторно подготовить диск постоянной памяти (см. Мы описанные выше шаги).

При устранении неполадок может потребоваться использовать **Remove-PmemDisk**, который удаляет диск конкретных постоянной памяти. Мы можем удалить все текущего постоянных дисков по:

```PowerShell
Get-PmemDisk | Remove-PmemDisk

cmdlet Remove-PmemDisk at command pipeline position 1
Supply values for the following parameters:
DiskNumber: 2

This will remove the persistent memory disk(s) from the system and will result in data loss.
Remove the persistent memory disk(s)?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
Removing the persistent memory disk. This may take a few moments.
```

Это важно отметить, что удаление диска постоянной памяти приведет к потере данных на этом диске.

Другой командлет, может потребоваться **Initialize PmemPhysicalDevice**, будет инициализировано область хранения метки на устройствах постоянный объем физической памяти. Это можно использовать для очистки info хранилища поврежден метки на устройствах постоянной памяти.

```PowerShell
Get-PmemPhysicalDevice | Initialize-PmemPhysicalDevice

This will initialize the label storage area on the physical persistent memory device(s) and will result in data loss.
Initializes the physical persistent memory device(s)?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
Initializing the physical persistent memory device. This may take a few moments.
Initializing the physical persistent memory device. This may take a few moments.
Initializing the physical persistent memory device. This may take a few moments.
Initializing the physical persistent memory device. This may take a few moments.
```

Важно отметить, что эту команду следует использовать в качестве последнего средства исправить постоянной памяти проблемы, связанные с. Это приведет к потере данных в постоянной памяти.

## <a name="see-also"></a>См. также

- [Общие сведения о дисковых хранилища](storage-spaces-direct-overview.md)
- [Управление работоспособностью памяти (NVDIMM-N) класса хранения в Windows](storage-class-memory-health.md)
- [Общие сведения о кэше](understand-the-cache.md)