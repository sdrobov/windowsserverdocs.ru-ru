---
title: Журнал производительности для дисков
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
Keywords: Storage Spaces Direct
ms.localizationpriority: medium
ms.openlocfilehash: d162275a885dac79e7efe749328ebdca471fcad1
ms.sourcegitcommit: 1533d994a6ddea54ac189ceb316b7d3c074307db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "1589761"
---
# <a name="performance-history-for-drives"></a>Журнал производительности для дисков

> Применимо к: Просмотр внутренних Windows Server

Этот подраздел истории [производительности для хранения пробелы прямое](performance-history.md) подробно журнал производительности, собранные для дисков. Журнал производительности доступна для каждого диска в подсистеме хранилища кластера, независимо от того, шины или типа носителя. Тем не менее не доступен для загрузки дисков операционной системы.

   > [!NOTE]
   > Журнал производительности нельзя собраны для дисков сервера, на котором не работает. Коллекция продолжит автоматически при сервер будет восстановлена.

## <a name="series-names-and-units"></a>Имена и единиц измерения

Эти серии сбора для каждого подходящими диска:

| Серия                          | Unit             |
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
| `physicaldisk.size.total`       |  байт            |
| `physicaldisk.size.used`        |  байт            |

## <a name="how-to-interpret"></a>Интерпретация

| Серия                          | Интерпретация                                                            |
|---------------------------------|-----------------------------------------------------------------------------|
| `physicaldisk.iops.read`        | Число операций чтения в секунду, выполнено, диске.                |
| `physicaldisk.iops.write`       | Число операций записи в секунду, выполнено, диске.               |
| `physicaldisk.iops.total`       | Общее число операций чтения и записи в секунду, выполнено, диске. |
| `physicaldisk.throughput.read`  | Количество данных, ознакомьтесь с диска в секунду.                            |
| `physicaldisk.throughput.write` | Количество данных, записи на диск в секунду.                           |
| `physicaldisk.throughput.total` | Общее количество данных, чтение и запись на диск в секунду.        |
| `physicaldisk.latency.read`     | Средняя задержка операций чтения с диска.                          |
| `physicaldisk.latency.write`    | Средняя задержка операций записи на диск.                           |
| `physicaldisk.latency.average`  | Средняя задержка все операции для или диска.                     |
| `physicaldisk.size.total`       | Общая емкость диска.                                    |
| `physicaldisk.size.used`        | Используемые емкость диска.                                     |

## <a name="where-they-come-from"></a>Откуда берется из

`iops.*`, `throughput.*`, И `latency.*` серии полученных от `Physical Disk` установки на том сервере, где подключен диск счетчика производительности, один экземпляр на диске. Эти счетчики измеряемую `partmgr.sys` и не включать много стека программного обеспечения Windows, ни любой переходов между сети. Они являются представителя производительность оборудования устройств.

| Серия                          | Счетчик исходных данных           |
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
   > Счетчики заданная в период времени, не выбрано. Например, если диск простоя в течение 9 секунд но завершается 30 операций ввода-вывода в десятой секунды его `physicaldisk.iops.total` будет записана в виде 3 операций ввода-вывода в секунду в среднем этот период 10 секунд. Это гарантирует журнал производительности захватывает все действия и надежна для помех.

`size.*` Серии полученных от `MSFT_PhysicalDisk` класса в WMI, один экземпляр на диске.

| Серия                          | Свойство Source        |
|---------------------------------|------------------------|
| `physicaldisk.size.total`       | `Size`                 |
| `physicaldisk.size.used`        | `VirtualDiskFootprint` |

## <a name="usage-in-powershell"></a>Об использовании в PowerShell

Командлет [Get-физический диск](https://docs.microsoft.com/powershell/module/storage/get-physicaldisk) :

```PowerShell
Get-PhysicalDisk -SerialNumber <SerialNumber> | Get-ClusterPerf
```

## <a name="see-also"></a>См. также

- [Журнал производительности для прямого пробелы хранилища](performance-history.md)
