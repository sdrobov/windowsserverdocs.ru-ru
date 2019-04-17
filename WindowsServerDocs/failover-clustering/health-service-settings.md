---
title: "Параметры службы работоспособности"
ms.prod: windows-server-threshold
manager: eldenc
ms.author: cosdar
ms.technology: storage-health-service
ms.topic: article
ms.assetid: 
author: cosmosdarwin
ms.date: 08/14/2017
ms.openlocfilehash: 569cf7ba30fd3f993394efd3735a56d116c067e0
ms.sourcegitcommit: 30fcae929ce7b611f5d3a5f8fee64b0299272110
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2017
---
# <a name="health-service-settings"></a>Параметры службы работоспособности
> Применяется к Windows Server 2016

Служба работоспособности — это новая функция в Windows Server 2016, которая улучшает качество повседневного наблюдения за и рабочей взаимодействие для кластеров под управлением дисковых пространств.

Многие из параметров, которые управляют поведением службы работоспособности, представлены в виде параметров. Можно изменить эти настройки интенсивности сбоев или действия, включить определенными параметрами, включения и выключения и многое другое.

Чтобы задать или изменить параметры, используйте следующий командлет PowerShell.

### <a name="usage"></a>Использование

```PowerShell
Get-StorageSubSystem Cluster* | Set-StorageHealthSetting -Name <SettingName> -Value <Value>  
```

#### <a name="example"></a>Пример

```PowerShell
Get-StorageSubSystem Cluster* | Set-StorageHealthSetting -Name "System.Storage.Volume.CapacityThreshold.Warning" -Value 70
```

### <a name="common-settings"></a>Общие параметры

Ниже перечислены некоторые часто измененные параметры вместе с их значения по умолчанию.

#### <a name="volume-capacity-threshold"></a>Пороговое значение емкость тома

```
"System.Storage.Volume.CapacityThreshold.Enabled"  = True
"System.Storage.Volume.CapacityThreshold.Warning"  = 80
"System.Storage.Volume.CapacityThreshold.Critical" = 90
```

#### <a name="pool-reserve-capacity-threshold"></a>Порог емкости пула резерв

```
"System.Storage.StoragePool.CheckPoolReserveCapacity.Enabled" = True
```

#### <a name="physical-disk-lifecycle"></a>Жизненного цикла физического диска

```
"System.Storage.PhysicalDisk.AutoPool.Enabled"                             = True
"System.Storage.PhysicalDisk.AutoRetire.OnLostCommunication.Enabled"       = True
"System.Storage.PhysicalDisk.AutoRetire.OnUnresponsive.Enabled"            = True
"System.Storage.PhysicalDisk.AutoRetire.DelayMs"                           = 900000 (i.e. 15 minutes)
"System.Storage.PhysicalDisk.Unresponsive.Reset.CountResetIntervalSeconds" = 360 (i.e. 60 minutes)
"System.Storage.PhysicalDisk.Unresponsive.Reset.CountAllowed"              = 3
```

#### <a name="supported-components-document"></a>Поддерживаемые компоненты документа

См. в предыдущем разделе.

#### <a name="firmware-rollout"></a>Выпуск встроенного по

```
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.SingleDrive.Enabled"       = True
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.Enabled"           = True
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.LongDelaySeconds"  = 604800 (i.e. 7 days)
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.ShortDelaySeconds" = 86400 (i.e. 1 day)
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.LongDelayCount"    = 1
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.FailureTolerance"  = 3
```

#### <a name="platform--quiescence"></a>Платформы и Quiescence

```
"Platform.Quiescence.MinDelaySeconds" = 120 (i.e. 2 minutes)
"Platform.Quiescence.MaxDelaySeconds" = 420 (i.e. 7 minutes)
```

#### <a name="metrics"></a>Метрики

```
"System.Reports.ReportingPeriodSeconds" = 1
```

#### <a name="debugging"></a>Отладка

```
"System.LogLevel" = 4
```

## <a name="see-also"></a>См. также:

- [Служба работоспособности в Windows Server 2016](health-service-overview.md)
- [Локальные дисковые пространства в Windows Server 2016](../storage/storage-spaces/storage-spaces-direct-overview.md)
