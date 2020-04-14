---
title: Журнал производительности для дисков
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: a6c6065b8d7963ada5d80844b270fe088eaa6e56
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859457"
---
# <a name="performance-history-for-drives"></a>Журнал производительности для дисков

> Область применения: Windows Server 2019

В этом подразделе [журнала производительности для Локальные дисковые пространства](performance-history.md) подробно описывается журнал производительности, собранный для дисков. Журнал производительности доступен для каждого диска в подсистеме хранения кластера, независимо от шины или типа носителя. Однако он недоступен для загрузочных дисков операционной системы.

   > [!NOTE]
   > Не удается собрать журнал производительности для дисков на недоступном сервере. Коллекция будет возобновлена автоматически при резервном копировании сервера.

## <a name="series-names-and-units"></a>Имена и единицы рядов

Эти серии собираются для каждого подходящего диска:

| Ряд                          | Единица измерения             |
|---------------------------------|------------------|
| `physicaldisk.iops.read`        | в секунду       |
| `physicaldisk.iops.write`       | в секунду       |
| `physicaldisk.iops.total`       | в секунду       |
| `physicaldisk.throughput.read`  | байт в секунду |
| `physicaldisk.throughput.write` | байт в секунду |
| `physicaldisk.throughput.total` | байт в секунду |
| `physicaldisk.latency.read`     | секунд          |
| `physicaldisk.latency.write`    | секунд          |
| `physicaldisk.latency.average`  | секунд          |
| `physicaldisk.size.total`       | байты            |
| `physicaldisk.size.used`        | байты            |

## <a name="how-to-interpret"></a>Как интерпретировать

| Ряд                          | Как интерпретировать                                                            |
|---------------------------------|-----------------------------------------------------------------------------|
| `physicaldisk.iops.read`        | Число операций чтения в секунду, выполненных диском.                |
| `physicaldisk.iops.write`       | Число операций записи в секунду, выполненных диском.               |
| `physicaldisk.iops.total`       | Общее число операций чтения или записи в секунду, выполненных диском. |
| `physicaldisk.throughput.read`  | Количество данных, считанных с диска в секунду.                            |
| `physicaldisk.throughput.write` | Количество данных, записываемых на диск в секунду.                           |
| `physicaldisk.throughput.total` | Общее количество данных, считанных или записанных на диск в секунду.        |
| `physicaldisk.latency.read`     | Средняя задержка операций чтения с диска.                          |
| `physicaldisk.latency.write`    | Средняя задержка операций записи на диск.                           |
| `physicaldisk.latency.average`  | Средняя задержка всех операций на диск или с него.                     |
| `physicaldisk.size.total`       | Общий объем хранилища диска.                                    |
| `physicaldisk.size.used`        | Используемая емкость хранилища диска.                                     |

## <a name="where-they-come-from"></a>Откуда они приходят

Ряды `iops.*`, `throughput.*`и `latency.*` собираются из счетчика производительности `Physical Disk`, установленного на сервере, на котором подключен диск, по одному экземпляру на диск. Эти счетчики измеряются `partmgr.sys` и не включают большую часть стека программного обеспечения Windows и других прыжков сети. Они представляют собой представление о производительности оборудования устройства.

| Ряд                          | Счетчик источника           |
|---------------------------------|--------------------------|
| `physicaldisk.iops.read`        | `Disk Reads/sec`         |
| `physicaldisk.iops.write`       | `Disk Writes/sec`        |
| `physicaldisk.iops.total`       | `Disk Transfers/sec`     |
| `physicaldisk.throughput.read`  | `Disk Read Bytes/sec`    |
| `physicaldisk.throughput.write` | `Disk Write Bytes/sec`   |
| `physicaldisk.throughput.total` | `Disk Bytes/sec`         |
| `physicaldisk.latency.read`     | `Avg. Disk sec/Read`     |
| `physicaldisk.latency.write`    | `Avg. Disk sec/Writes`   |
| `physicaldisk.latency.average`  | `Avg. Disk sec/Transfer` |

   > [!NOTE]
   > Счетчики измеряются для всего интервала, а не для выборки. Например, если диск бездействует в течение 9 секунд, но завершает 30 IOs в десятой секунде, его `physicaldisk.iops.total` записываются в среднем 3 IOs в секунду в течение этого 10-секундного интервала. Это гарантирует, что журнал производительности захватывает все действия и является надежным для шума.

`size.*` серии собираются из класса `MSFT_PhysicalDisk` в WMI, по одному экземпляру на диск.

| Ряд                          | Source - свойство        |
|---------------------------------|------------------------|
| `physicaldisk.size.total`       | `Size`                 |
| `physicaldisk.size.used`        | `VirtualDiskFootprint` |

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте командлет [Get-физический](https://docs.microsoft.com/powershell/module/storage/get-physicaldisk) :

```PowerShell
Get-PhysicalDisk -SerialNumber <SerialNumber> | Get-ClusterPerf
```

## <a name="see-also"></a>См. также:

- [Журнал производительности для Локальные дисковые пространства](performance-history.md)
