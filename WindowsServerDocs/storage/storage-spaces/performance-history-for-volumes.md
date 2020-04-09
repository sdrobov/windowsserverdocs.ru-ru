---
title: Журнал производительности для томов
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/09/2018
ms.localizationpriority: medium
ms.openlocfilehash: 5f6acf062d2dba7c2a1a04d8a3f7cb4d7bd51a4d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856137"
---
# <a name="performance-history-for-volumes"></a>Журнал производительности для томов

> Область применения: Windows Server 2019

В этом подразделе [журнала производительности для Локальные дисковые пространства](performance-history.md) подробно описывается журнал производительности, собранный для томов. Журнал производительности доступен для каждого общий том кластера (CSV) в кластере. Однако он недоступен для загрузочных томов ОС и других хранилищ, отличных от CSV.

   > [!NOTE]
   > Запуск сбора для вновь созданных или переименованных томов может занять несколько минут.

## <a name="series-names-and-units"></a>Имена и единицы рядов

Эти серии собираются для каждого подходящего тома:

| Ряд                    | Единица измерения             |
|---------------------------|------------------|
| `volume.iops.read`        | в секунду       |
| `volume.iops.write`       | в секунду       |
| `volume.iops.total`       | в секунду       |
| `volume.throughput.read`  | байт в секунду |
| `volume.throughput.write` | байт в секунду |
| `volume.throughput.total` | байт в секунду |
| `volume.latency.read`     | секунд          |
| `volume.latency.write`    | секунд          |
| `volume.latency.average`  | секунд          |
| `volume.size.total`       | байты            |
| `volume.size.available`   | байты            |

## <a name="how-to-interpret"></a>Как интерпретировать

| Ряд                    | Как интерпретировать                                                              |
|---------------------------|-------------------------------------------------------------------------------|
| `volume.iops.read`        | Число операций чтения в секунду, выполненных этим томом.                |
| `volume.iops.write`       | Число операций записи в секунду, выполненных этим томом.               |
| `volume.iops.total`       | Общее число операций чтения или записи в секунду, выполненных этим томом. |
| `volume.throughput.read`  | Количество данных, считанных из этого тома за секунду.                            |
| `volume.throughput.write` | Количество данных, записываемых в этот том в секунду.                           |
| `volume.throughput.total` | Общее количество данных, считанных или записанных в этот том в секунду.        |
| `volume.latency.read`     | Средняя задержка операций чтения с этого тома.                          |
| `volume.latency.write`    | Средняя задержка операций записи на этот том.                           |
| `volume.latency.average`  | Средняя задержка всех операций до или из этого тома.                     |
| `volume.size.total`       | Общая емкость хранилища тома.                                     |
| `volume.size.available`   | Доступная емкость хранилища тома.                                 |

## <a name="where-they-come-from"></a>Откуда они приходят

Ряды `iops.*`, `throughput.*`и `latency.*` собираются из набора счетчиков производительности `Cluster CSVFS`. Каждый сервер в кластере имеет экземпляр для каждого тома CSV, независимо от его владельца. Журнал производительности, записанный для `MyVolume` тома — это совокупность экземпляров `MyVolume` на каждом сервере в кластере.

| Ряд                    | Счетчик источника         |
|---------------------------|------------------------|
| `volume.iops.read`        | `Reads/sec`            |
| `volume.iops.write`       | `Writes/sec`           |
| `volume.iops.total`       | *сумма приведенной выше*     |
| `volume.throughput.read`  | `Read bytes/sec`       |
| `volume.throughput.write` | `Write bytes/sec`      |
| `volume.throughput.total` | *сумма приведенной выше*     |
| `volume.latency.read`     | `Avg. sec/Read`        |
| `volume.latency.write`    | `Avg. sec/Write`       |
| `volume.latency.average`  | *среднее значение указанного выше* |

   > [!NOTE]
   > Счетчики измеряются для всего интервала, а не для выборки. Например, если объем бездействия составляет 9 секунд, но завершает 30 IOs в десятой секунде, его `volume.iops.total` записываются в среднем 3 IOs в секунду в течение этого 10-секундного интервала. Это гарантирует, что журнал производительности захватывает все действия и является надежным для шума.

   > [!TIP]
   > Это те же счетчики, которые используются в популярной платформе тестирования производительности [виртуальной машины](https://github.com/Microsoft/diskspd/blob/master/Frameworks/VMFleet/watch-cluster.ps1) .

`size.*` серии собираются из класса `MSFT_Volume` в WMI, по одному экземпляру на том.

| Ряд                    | Source - свойство |
|---------------------------|-----------------|
| `volume.size.total`       | `Size`          |
| `volume.size.available`   | `SizeRemaining` |

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте командлет [Get-Volume](https://docs.microsoft.com/powershell/module/storage/get-volume) :

```PowerShell
Get-Volume -FriendlyName <FriendlyName> | Get-ClusterPerf
```

## <a name="see-also"></a>См. также:

- [Журнал производительности для Локальные дисковые пространства](performance-history.md)
