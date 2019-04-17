---
title: Журнал производительности для томов
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/09/2018
Keywords: Storage Spaces Direct
ms.localizationpriority: medium
ms.openlocfilehash: fea1d3d67ab96d95b1699e8ac0129dba698477fe
ms.sourcegitcommit: 1533d994a6ddea54ac189ceb316b7d3c074307db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "1589710"
---
# <a name="performance-history-for-volumes"></a>Журнал производительности для томов

> Применимо к: Просмотр внутренних Windows Server

Этот подраздел истории [производительности для хранения пробелы прямое](performance-history.md) подробно журнал производительности, собранные для тома. Журнал производительности — доступны для каждого кластера общих тома (CSV) в кластере. Тем не менее, он недоступен для операционной системы загрузки тома, ни другие хранилища не CSV.

   > [!NOTE]
   > Может занять несколько минут для семейства сайтов для начала для созданного или переименованной тома.

## <a name="series-names-and-units"></a>Имена и единиц измерения

Эти серии сбора для каждого подходящими тома:

| Серия                    | Unit             |
|---------------------------|------------------|
| `volume.iops.read`        | в секунду       |
| `volume.iops.write`       | в секунду       |
| `volume.iops.total`       | в секунду       |
| `volume.throughput.read`  | байт в секунду |
| `volume.throughput.write` | байт в секунду |
| `volume.throughput.total` | байт в секунду |
| `volume.latency.read`     | секунды          |
| `volume.latency.write`    | секунды          |
| `volume.latency.average`  | секунды          |
| `volume.size.total`       |  байт            |
| `volume.size.available`   |  байт            |

## <a name="how-to-interpret"></a>Интерпретация

| Серия                    | Интерпретация                                                              |
|---------------------------|-------------------------------------------------------------------------------|
| `volume.iops.read`        | Число операций чтения в секунду завершено с этого тома.                |
| `volume.iops.write`       | Число операций записи в секунду завершено с этого тома.               |
| `volume.iops.total`       | Общее число операций чтения и записи в секунду завершено с этого тома. |
| `volume.throughput.read`  | Количество данных, ознакомьтесь с этой тома в секунду.                            |
| `volume.throughput.write` | Количество данных, записанных на том в секунду.                           |
| `volume.throughput.total` | Общее количество данных, чтение и запись для этого тома в секунду.        |
| `volume.latency.read`     | Средняя задержка операций чтения с этого тома.                          |
| `volume.latency.write`    | Средняя задержка операций записи на том.                           |
| `volume.latency.average`  | Средняя задержка все операции или из этого тома.                     |
| `volume.size.total`       | Общая емкость тома.                                     |
| `volume.size.available`   | Доступные емкость тома.                                 |

## <a name="where-they-come-from"></a>Откуда берется из

`iops.*`, `throughput.*`, И `latency.*` серии полученных от `Cluster CSVFS` набора счетчиков производительности. Каждый сервер в кластере имеет экземпляр для каждого тома, CSV, независимо от владельца. Запись журнала производительности для многопользовательской `MyVolume` — это статистической обработки `MyVolume` экземпляры на каждом сервере в кластере.

| Серия                    | Счетчик исходных данных         |
|---------------------------|------------------------|
| `volume.iops.read`        | `Reads/sec`            |
| `volume.iops.write`       | `Writes/sec`           |
| `volume.iops.total`       | *Сумма из перечисленных выше*     |
| `volume.throughput.read`  | `Read bytes/sec`       |
| `volume.throughput.write` | `Write bytes/sec`      |
| `volume.throughput.total` | *Сумма из перечисленных выше*     |
| `volume.latency.read`     | `Avg. sec/Read`        |
| `volume.latency.write`    | `Avg. sec/Write`       |
| `volume.latency.average`  | *Среднее число из перечисленных выше* |

   > [!NOTE]
   > Счетчики заданная в период времени, не выбрано. Например, если том простоя в течение 9 секунд но завершается 30 операций ввода-вывода в десятой секунды его `volume.iops.total` будет записана в виде 3 операций ввода-вывода в секунду в среднем этот период 10 секунд. Это гарантирует журнал производительности захватывает все действия и надежна для помех.

   > [!TIP]
   > Это же счетчики используется инфраструктурой тестирования производительности популярные [Флота виртуальной Машины](https://github.com/Microsoft/diskspd/blob/master/Frameworks/VMFleet/watch-cluster.ps1) .

`size.*` Серии полученных от `MSFT_Volume` класс в одном экземпляре на том WMI.

| Серия                    | Свойство Source |
|---------------------------|-----------------|
| `volume.size.total`       | `Size`          |
| `volume.size.available`   | `SizeRemaining` |

## <a name="usage-in-powershell"></a>Об использовании в PowerShell

Командлет [Get-громкость](https://docs.microsoft.com/powershell/module/storage/get-volume) :

```PowerShell
Get-Volume -FriendlyName <FriendlyName> | Get-ClusterPerf
```

## <a name="see-also"></a>См. также

- [Журнал производительности для прямого пробелы хранилища](performance-history.md)
