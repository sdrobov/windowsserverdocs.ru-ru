---
title: Журнал производительности для дисков
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
Keywords: Локальные дисковые пространства
ms.localizationpriority: medium
ms.openlocfilehash: d162275a885dac79e7efe749328ebdca471fcad1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879195"
---
# <a name="performance-history-for-drives"></a>Журнал производительности для дисков

> Область применения. Сборка из программы предварительной оценки Windows Server

Этот подраздел из [журнал производительности дисковых](performance-history.md) подробно описывается журнал производительности, собранных для дисков. Для каждого диска в подсистеме хранилища кластера, независимо от шины доступен журнал производительности или тип мультимедиа. Тем не менее он доступен для загрузки дисков операционной системы.

   > [!NOTE]
   > Журнал производительности не может собирать для дисков на сервере, который не работает. Коллекция будет возобновлена автоматически, когда сервер возобновляет работу.

## <a name="series-names-and-units"></a>Имена рядов и единицы

Для каждого диска право собираются этих рядов.

| серии                          | Единица измерения             |
|---------------------------------|------------------|
| `physicaldisk.iops.read`        | в секунду       |
| `physicaldisk.iops.write`       | в секунду       |
| `physicaldisk.iops.total`       | в секунду       |
| `physicaldisk.throughput.read`  | байт в секунду |
| `physicaldisk.throughput.write` | байт в секунду |
| `physicaldisk.throughput.total` | байт в секунду |
| `physicaldisk.latency.read`     | секунды          |
| `physicaldisk.latency.write`    | секунды          |
| `physicaldisk.latency.average`  | секунды          |
| `physicaldisk.size.total`       | байт            |
| `physicaldisk.size.used`        | байт            |

## <a name="how-to-interpret"></a>Способ интерпретации

| серии                          | Способ интерпретации                                                            |
|---------------------------------|-----------------------------------------------------------------------------|
| `physicaldisk.iops.read`        | Количество операций чтения в секунду, выполненных на диске.                |
| `physicaldisk.iops.write`       | Количество операций записи в секунду, выполненных на диске.               |
| `physicaldisk.iops.total`       | Общее число операций чтения или записи в секунду, выполненных на диске. |
| `physicaldisk.throughput.read`  | Количество данных, считанных с диска в секунду.                            |
| `physicaldisk.throughput.write` | Количество данных, записанных на диск в секунду.                           |
| `physicaldisk.throughput.total` | Общее количество данных считывается или записывается на диск в секунду.        |
| `physicaldisk.latency.read`     | Средняя задержка операций чтения с диска.                          |
| `physicaldisk.latency.write`    | Средняя задержка операций записи на диск.                           |
| `physicaldisk.latency.average`  | Среднее по всем операциям, или с диска.                     |
| `physicaldisk.size.total`       | Общая емкость хранения диска.                                    |
| `physicaldisk.size.used`        | Объем используемой памяти диска.                                     |

## <a name="where-they-come-from"></a>Откуда они берутся

`iops.*`, `throughput.*`, И `latency.*` ряда собираются из `Physical Disk` набор на сервере, которой подключен диск счетчиков производительности, по одному экземпляру каждого диска. Эти счетчики измеряются с `partmgr.sys` и не включают большую часть стека программного обеспечения Windows, ни любой сетевых переходов. Это представление производительности оборудования устройства.

| серии                          | Счетчик источника           |
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
   > Счетчики измеряемый в течение всего интервала, не попали в выборку. Например, если диск является простое 9 секунд но завершается 30 IOs в десятой секунды, его `physicaldisk.iops.total` будут записываться как 3 операций ввода-вывода в секунду в среднем за этот 10-секундный интервал. Это гарантирует, что его журнал производительности записывает все действия и надежна для шума.

`size.*` Ряда собираются из `MSFT_PhysicalDisk` класса в WMI, один экземпляр каждого диска.

| серии                          | Свойство Source        |
|---------------------------------|------------------------|
| `physicaldisk.size.total`       | `Size`                 |
| `physicaldisk.size.used`        | `VirtualDiskFootprint` |

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте [Get-PhysicalDisk](https://docs.microsoft.com/powershell/module/storage/get-physicaldisk) командлета:

```PowerShell
Get-PhysicalDisk -SerialNumber <SerialNumber> | Get-ClusterPerf
```

## <a name="see-also"></a>См. также

- [Журнал производительности для дисковых пространств](performance-history.md)
