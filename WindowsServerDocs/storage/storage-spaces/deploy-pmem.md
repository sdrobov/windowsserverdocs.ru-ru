---
title: Изучение и развертывание постоянной памяти
description: Подробные сведения о том, что такое постоянная память и как ее настроить с помощью локальных дисковых пространств в Windows Server 2019.
keywords: Локальные дисковые пространства, энергоустойчивая память, pMem, хранилище, S2D
ms.assetid: ''
ms.prod: ''
ms.author: adagashe
ms.technology: storage-spaces
ms.topic: article
author: adagashe
ms.date: 3/26/2019
ms.localizationpriority: ''
ms.openlocfilehash: 497fa201c500919fc857d25166d37ce87613d0f0
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70872007"
---
---
# <a name="understand-and-deploy-persistent-memory"></a>Изучение и развертывание постоянной памяти

>Относится к: Windows Server 2019

Постоянная память (или PMem) — это новый тип технологии памяти, обеспечивающий уникальную комбинацию доступной большой емкости и сохраняемости. Этот раздел содержит сведения о PMem и действиях по его развертыванию с помощью Windows Server 2019 с Локальные дисковые пространства.

## <a name="background"></a>Фоновый

PMem — это тип долговременной DRAM (NVDIMM), имеющий скорость DRAM, но сохраняющий содержимое памяти через циклы электропитания (содержимое памяти остается даже при отключении питания системы в случае неожиданного отключения питания, инициирования пользователем завершения работы, сбоя системы, и т. д.). По этой причине возобновление с того места, на котором вы остановились, выполняется значительно быстрее, так как содержимое ОЗУ не требуется перезагружать. Другая уникальная характеристика состоит в том, что PMem является байтовой адресацией. Это означает, что вы также можете использовать его в качестве хранилища (поэтому вы можете слышать, что PMem называется памятью класса хранения).


Чтобы увидеть некоторые из этих преимуществ, давайте взглянем на эту демонстрацию от Microsoft Ignite 2018:

[![Демонстрация Microsoft Ignite 2018 pMem](http://img.youtube.com/vi/8WMXkMLJORc/0.jpg)](http://www.youtube.com/watch?v=8WMXkMLJORc)

Любая система хранения, обеспечивающая отказоустойчивость, обязательно создает распределенные копии операций записи, которые должны пройти по сети и возвращающие усиление записи в серверную часть. По этой причине абсолютные значения производительности операций ввода-вывода в секунду обычно дополняются только чтением, особенно если в системе хранения используются стандартные оптимизации для чтения из локальной копии, когда это возможно, что Локальные дисковые пространства.

**С 100% операций чтения кластер доставляет 13 798 674 операций ввода-вывода.**

![снимок экрана 13.7 m записи операций ввода-вывода](media/deploy-pmem/iops-record.png)

При внимательном просмотре видео вы заметите, что сатвхат еще больше Жава — это задержка: даже при более чем 13,7 м в секунду, файловая система в Windows сообщает о задержке, которая постоянно меньше 40 μс! (Это символ в микросекундах, одна миллионная доля секунды.) Это порядок, более быстрый, чем стандартные поставщики Flash, которые в настоящее время объявляются сегодня.

Вместе, Локальные дисковые пространства в Windows Server 2019 и Intel® Оптане™ постоянного энергонезависимой памятью, обеспечивают рекордную производительность. Этот ХЦИный тест производительности более 13.7 M операций ввода-вывода в секунду с прогнозируемой и крайне низкой задержкой является более чем удвоенным нашим предыдущим отраслевым показателем производительности 6.7 M операций ввода-вывода в секунду. Более того, на этот раз нам потребовалось всего 12 узлов серверов, 25% менее двух лет назад.

![Выигрыш в операциях ввода-вывода](media/deploy-pmem/iops-gains.png)

Используемое оборудование — это 12-серверный кластер, использующий три и разделенные тома ReFS, **12** x Intel® S2600WFT, **384 гиб** Memory, 2 x 28 — Core "КАСКАДЕЛАКЕ", **1,5 ТБ** Intel® оптане™ контроллер домена с постоянным объемом памяти в кэше, **32 ТБ** NVMe ( 4 x 8 ТБ Intel® DC P4510) как емкость, **2** x Mellanox ConnectX-4 25 Гбит/с

В таблице ниже приведены полные показатели производительности. 

| Задание                   | Производительность         |
|-----------------------------|---------------------|
| 4 КБ 100% случайное чтение         | 13 800 000 операций ввода-вывода   |
| 4 КБ 90/10% произвольное чтение/запись | 9 450 000 операций ввода-вывода   |
| 2 МБ последовательного чтения         | пропускная способность 549 ГБ/с |

### <a name="supported-hardware"></a>Поддерживаемое оборудование

В таблице ниже показано поддерживаемое оборудование энергонезависимой памяти для Windows Server 2019 и Windows Server 2016. Обратите внимание, что Intel Оптане специально поддерживает как режим памяти, так и режим приложения в прямом направлении. Windows Server 2019 поддерживает операции в смешанном режиме.

| Технология энергоустойчивой памяти                                      | Windows Server 2016 | Windows Server 2019 |
|-------------------------------------------------------------------|--------------------------|--------------------------|
| **Устройство NVDIMM-N** в режиме "приложение — прямое"                                       | Поддерживается                | Поддерживается                |
| **Intel оптане™ постоянный объем памяти контроллера домена** в режиме "приложение — прямое"             | Не поддерживается            | Поддерживается                |
| **Intel оптане™ постоянный объем памяти контроллера домена** в режиме двух уровней памяти (2LM) | Не поддерживается            | Поддерживается                |

Теперь давайте рассмотрим настройку энергонезависимой памяти.

## <a name="interleave-sets"></a>Наборы чередования

### <a name="understanding-interleave-sets"></a>Основные сведения о наборах чередования

Вспомним, что устройство NVDIMM-N находится в стандартном гнезде DIMM (память), помещая данные ближе к процессору (таким образом уменьшая задержку и получая лучшую производительность). Для этого набор чередования имеет значение, когда два или более Нвдиммс создают N-направленный набор чередования для предоставления чередующихся операций чтения и записи для повышения пропускной способности. Наиболее распространенные настройки — 2-или 4-направленное.

Чередующиеся наборы часто можно создавать в BIOS платформы, чтобы несколько устройств энергонезависимой памяти отображались как один логический диск для Windows Server. Каждый логический диск энергонезависимой памяти содержит набор физических устройств с чередованием, выполняя:

```PowerShell
Get-PmemDisk
```

Ниже приведен пример выходных данных.

```
DiskNumber Size   HealthStatus AtomicityType CanBeRemoved PhysicalDeviceIds UnsafeShutdownCount
---------- ----   ------------ ------------- ------------ ----------------- -------------------
2          252 GB Healthy      None          True         {20, 120}         0
3          252 GB Healthy      None          True         {1020, 1120}      0
```

Как видите, логический диск pMem #2 имеет физические устройства Id20 и Id120, а логический диск pMem #3 имеет физические устройства Id1020 и Id1120. Мы также можем передать для Get-Пмемфисикалдевице конкретный диск pMem, чтобы получить все его физические Нвдиммс в наборе чередования, как показано ниже.


```PowerShell
(Get-PmemDisk)[0] | Get-PmemPhysicalDevice
```

Ниже приведен пример выходных данных.

```
DeviceId DeviceType           HealthStatus OperationalStatus PhysicalLocation FirmwareRevision Persistent memory size Volatile memory size
-------- ----------           ------------ ----------------- ---------------- ---------------- ---------------------- --------------------
20       Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_C1     102005310        126 GB                 0 GB
120      Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_F1     102005310        126 GB                 0 GB
```

### <a name="configuring-interleave-sets"></a>Настройка наборов чередования

Чтобы настроить набор чередования, выполните следующий командлет PowerShell:

```PowerShell
Get-PmemUnusedRegion

RegionId TotalSizeInBytes DeviceId
-------- ---------------- --------
       1     270582939648 {20, 120}
       3     270582939648 {1020, 1120}
```

Отображаются все области памяти, не назначенные логическому диску энергонезависимой памяти в системе.

Чтобы просмотреть все сведения о постоянных устройствах памяти в системе, включая тип устройства, расположение, работоспособность и состояние работы, и т. д., можно выполнить следующий командлет на локальном сервере:

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

Так как мы получили доступ к неиспользуемому региону pMem, можно создать новые диски энергонезависимой памяти. Мы можем создать несколько дисков энергонезависимой памяти с помощью неиспользуемых регионов:

```PowerShell
Get-PmemUnusedRegion | New-PmemDisk
Creating new persistent memory disk. This may take a few moments.
```

После это сделано, можно увидеть результаты, выполнив следующую команду:

```PowerShell
Get-PmemDisk

DiskNumber Size   HealthStatus AtomicityType CanBeRemoved PhysicalDeviceIds UnsafeShutdownCount
---------- ----   ------------ ------------- ------------ ----------------- -------------------
2          252 GB Healthy      None          True         {20, 120}         0
3          252 GB Healthy      None          True         {1020, 1120}      0
```

Стоит отметить, что можно было выполнить **Get-физический диск | Где MediaType-EQ SCM** вместо **Get-пмемдиск** для получения тех же результатов. Созданный диск энергонезависимой памяти соответствует 1:1 дискам, отображаемым в PowerShell и центре администрирования Windows.

### <a name="using-persistent-memory-for-cache-or-capacity"></a>Использование энергонезависимой памяти для кэша или емкости

Локальные дисковые пространства в Windows Server 2019 поддерживает использование постоянной памяти в качестве диска кэша или емкости. Дополнительные сведения о настройке дисков кэша и емкости см. в этой [документации](understand-the-cache.md) .

## <a name="creating-a-dax-volume"></a>Создание тома DAX

### <a name="understanding-dax"></a>Основные сведения об DAX

Существует два способа доступа к энергонезависимой памяти. Подробные сведения.

1. **Прямой доступ (DAX)** , который действует как память для получения наименьшей задержки. Приложение непосредственно изменяет постоянную память, минуя стек. Обратите внимание, что этот параметр можно использовать только с файловой системой NTFS.
2. **Блокировать доступ**, который действует как хранилище для совместимости приложений. Данные проходят через стек в этой настройке, и это можно использовать с NTFS и ReFS.

Пример можно увидеть ниже:

![Стек DAX](media/deploy-pmem/dax.png)

### <a name="configuring-dax"></a>Настройка DAX

Чтобы создать том DAX в энергонезависимой памяти, необходимо использовать командлеты PowerShell. С помощью параметра **-исдакс** можно отформатировать том для включения DAX.

```PowerShell
Format-Volume -IsDax:$true
```

Следующий фрагмент кода поможет создать том DAX на диске энергонезависимой памяти.

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

При использовании постоянной памяти существует несколько отличий в работе мониторинга.

1. Постоянная память не создает счетчики производительности физических дисков, поэтому она не будет отображаться на диаграммах в центре администрирования Windows.
2. Постоянная память не создает данные Storport 505, поэтому вы не будете получать упреждающее обнаружение выбросов.

Помимо этого, процесс мониторинга аналогичен любому другому физическому диску. Вы можете запросить работоспособность диска с энергонезависимой памятью, выполнив команду:

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

**Хеалсстатус** показывает, является ли диск энергонезависимой памяти работоспособным. **Унсафешутдовнкаунт** отслеживает количество завершений работы, которые могут привести к потере данных на этом логическом диске. Это сумма счетчика ненадежного завершения работы всех базовых устройств с постоянной памятью на этом диске. Для запроса сведений о работоспособности можно также использовать приведенные ниже команды. Параметры **OperationalStatus** и **оператионалдетаилс** предоставляют дополнительные сведения о состоянии работоспособности.

Чтобы запросить работоспособность устройства энергонезависимой памяти, выполните следующие действия.

```PowerShell
Get-PmemPhysicalDevice

DeviceId DeviceType           HealthStatus OperationalStatus PhysicalLocation FirmwareRevision Persistent memory size Volatile memory size
-------- ----------           ------------ ----------------- ---------------- ---------------- ---------------------- --------------------
1020     Intel INVDIMM device Healthy      {Ok}              CPU2_DIMM_C1     102005310        126 GB                 0 GB
1120     Intel INVDIMM device Healthy      {Ok}              CPU2_DIMM_F1     102005310        126 GB                 0 GB
120      Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_F1     102005310        126 GB                 0 GB
20       Intel INVDIMM device Unhealthy    {HardwareError}   CPU1_DIMM_C1     102005310        126 GB                 0 GB
```

Это показывает, какое устройство энергонезависимой памяти неработоспособно. Неработоспособное устройство (**DeviceID**) 20 соответствует регистру в приведенном выше примере. **Фисикаллокатион** из BIOS может помочь определить, какое устройство энергонезависимой памяти находится в состоянии сбоя.

## <a name="replacing-persistent-memory"></a>Замена энергонезависимой памяти

Выше мы рассказано, как просмотреть состояние работоспособности энергонезависимой памяти. Если необходимо заменить неисправный модуль, потребуется повторно настроить диск энергонезависимой памяти (см. действия, описанные выше).

При устранении неполадок может потребоваться использовать **Remove-пмемдиск**, который удаляет конкретный диск энергонезависимой памяти. Мы можем удалить все текущие постоянные диски, выполнив следующие действия.

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

Важно отметить, что удаление диска энергонезависимой памяти приведет к утере данных на этом диске.

Другой командлет, возможно, потребуется **инициализировать-пмемфисикалдевице**, который инициализирует область хранения меток на физических устройствах энергонезависимой памяти. Это можно использовать для очистки поврежденных сведений о хранилище меток на устройствах энергонезависимой памяти.

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

Важно отметить, что эта команда должна использоваться в качестве последнего средства для устранения проблем, связанных с постоянной памятью. Это приведет к утрате данных в постоянную память.

## <a name="see-also"></a>См. также

- [Обзор Локальные дисковые пространства](storage-spaces-direct-overview.md)
- [Управление работоспособностью памяти класса хранилища (NVDIMM-N) в Windows](storage-class-memory-health.md)
- [Общие сведения о кэше](understand-the-cache.md)