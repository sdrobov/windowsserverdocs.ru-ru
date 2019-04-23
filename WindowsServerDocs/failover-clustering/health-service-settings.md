---
title: Параметры службы работоспособности
ms.prod: windows-server-threshold
manager: eldenc
ms.author: cosdar
ms.technology: storage-health-service
ms.topic: article
ms.assetid: ''
author: cosmosdarwin
ms.date: 08/14/2017
ms.openlocfilehash: 569cf7ba30fd3f993394efd3735a56d116c067e0
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858335"
---
# <a name="health-service-settings"></a>Параметры службы работоспособности
> Область применения: Windows Server 2016

Служба работоспособности — это новая функция в Windows Server 2016, которая улучшает ежедневного мониторинга и опыт эксплуатации кластеров дисковыми пространствами.

Многие из параметров, которые управляют поведением службы работоспособности, предоставляются как параметры. Можно изменить эти настройки интенсивность ошибок или действия, включите определенными параметрами, включить или выключить и многое другое.

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

Ниже перечислены некоторые часто редактируемых параметры вместе со значениями по умолчанию.

#### <a name="volume-capacity-threshold"></a>Пороговое значение емкости тома

```
"System.Storage.Volume.CapacityThreshold.Enabled"  = True
"System.Storage.Volume.CapacityThreshold.Warning"  = 80
"System.Storage.Volume.CapacityThreshold.Critical" = 90
```

#### <a name="pool-reserve-capacity-threshold"></a>Пороговое значение резерва емкости для пула

```
"System.Storage.StoragePool.CheckPoolReserveCapacity.Enabled" = True
```

#### <a name="physical-disk-lifecycle"></a>Жизненный цикл физического диска

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

#### <a name="firmware-rollout"></a>Развертывание встроенного по

```
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.SingleDrive.Enabled"       = True
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.Enabled"           = True
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.LongDelaySeconds"  = 604800 (i.e. 7 days)
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.ShortDelaySeconds" = 86400 (i.e. 1 day)
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.LongDelayCount"    = 1
"System.Storage.PhysicalDisk.AutoFirmwareUpdate.RollOut.FailureTolerance"  = 3
```

#### <a name="platform--quiescence"></a>Платформа / замороженной

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

## <a name="see-also"></a>См. также

- [Служба работоспособности в Windows Server 2016](health-service-overview.md)
- [Дисковые пространства в Windows Server 2016](../storage/storage-spaces/storage-spaces-direct-overview.md)
