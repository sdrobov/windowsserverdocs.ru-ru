---
title: Журнал производительности для тома
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/09/2018
Keywords: Локальные дисковые пространства
ms.localizationpriority: medium
ms.openlocfilehash: fea1d3d67ab96d95b1699e8ac0129dba698477fe
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882955"
---
# <a name="performance-history-for-volumes"></a>Журнал производительности для тома

> Область применения. Сборка из программы предварительной оценки Windows Server

Этот подраздел из [журнал производительности дисковых](performance-history.md) подробно описывается журнал производительности, собранных для томов. Журнал производительности доступен для каждого общего тома кластера (CSV) в кластере. Тем не менее, он доступен не для операционной системы загрузки тома или любым другим хранилищем, не являющееся CSV.

   > [!NOTE]
   > Он может занять несколько минут для коллекции для начала для вновь созданных или переименован томов.

## <a name="series-names-and-units"></a>Имена рядов и единицы

Этих рядов собираются для каждого тома, соответствующие:

| серии                    | Единица измерения             |
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
| `volume.size.total`       | байт            |
| `volume.size.available`   | байт            |

## <a name="how-to-interpret"></a>Способ интерпретации

| серии                    | Способ интерпретации                                                              |
|---------------------------|-------------------------------------------------------------------------------|
| `volume.iops.read`        | Количество операций чтения в секунду, выполненных этого тома.                |
| `volume.iops.write`       | Количество операций записи в секунду, выполненных этого тома.               |
| `volume.iops.total`       | Общее число операций чтения или записи в секунду, выполненных этого тома. |
| `volume.throughput.read`  | Количество данных, считанных из этого тома в секунду.                            |
| `volume.throughput.write` | Количество данных, записанных на этот том в секунду.                           |
| `volume.throughput.total` | Общее количество данных считывается или записывается на этот том в секунду.        |
| `volume.latency.read`     | Средняя задержка операций чтения с этого тома.                          |
| `volume.latency.write`    | Средняя задержка операций записи на этот том.                           |
| `volume.latency.average`  | Среднее по всем операциям, или из этого тома.                     |
| `volume.size.total`       | Общая емкость хранения тома.                                     |
| `volume.size.available`   | Доступное хранилище объем тома.                                 |

## <a name="where-they-come-from"></a>Откуда они берутся

`iops.*`, `throughput.*`, И `latency.*` ряда собираются из `Cluster CSVFS` набор счетчиков производительности. Каждый сервер в кластере имеется экземпляр для каждого тома CSV, независимо от владельца. Журнал производительности записываются для тома `MyVolume` — это совокупность `MyVolume` экземпляры на каждом сервере в кластере.

| серии                    | Счетчик источника         |
|---------------------------|------------------------|
| `volume.iops.read`        | `Reads/sec`            |
| `volume.iops.write`       | `Writes/sec`           |
| `volume.iops.total`       | *суммы выше*     |
| `volume.throughput.read`  | `Read bytes/sec`       |
| `volume.throughput.write` | `Write bytes/sec`      |
| `volume.throughput.total` | *суммы выше*     |
| `volume.latency.read`     | `Avg. sec/Read`        |
| `volume.latency.write`    | `Avg. sec/Write`       |
| `volume.latency.average`  | *Среднее для указанных выше* |

   > [!NOTE]
   > Счетчики измеряемый в течение всего интервала, не попали в выборку. Например, если том простоя в течение 9 секунд но завершается 30 IOs в десятой секунды, его `volume.iops.total` будут записываться как 3 операций ввода-вывода в секунду в среднем за этот 10-секундный интервал. Это гарантирует, что его журнал производительности записывает все действия и надежна для шума.

   > [!TIP]
   > Это те же счетчики, используемые популярного [Fleet виртуальной Машины](https://github.com/Microsoft/diskspd/blob/master/Frameworks/VMFleet/watch-cluster.ps1) framework теста производительности.

`size.*` Ряда собираются из `MSFT_Volume` класса в WMI, один экземпляр каждого тома.

| серии                    | Свойство Source |
|---------------------------|-----------------|
| `volume.size.total`       | `Size`          |
| `volume.size.available`   | `SizeRemaining` |

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте [Get-Volume](https://docs.microsoft.com/powershell/module/storage/get-volume) командлета:

```PowerShell
Get-Volume -FriendlyName <FriendlyName> | Get-ClusterPerf
```

## <a name="see-also"></a>См. также

- [Журнал производительности для дисковых пространств](performance-history.md)
