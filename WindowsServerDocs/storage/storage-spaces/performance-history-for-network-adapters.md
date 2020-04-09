---
title: Журнал производительности для сетевых адаптеров
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: e2379ce540cb26c02bc79f591d2a597874ab287c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856217"
---
# <a name="performance-history-for-network-adapters"></a>Журнал производительности для сетевых адаптеров

> Область применения: Windows Server 2019

Этот подраздел [журнала производительности для Локальные дисковые пространства](performance-history.md) подробно описывает журнал производительности, собранный для сетевых адаптеров. Журнал производительности сетевого адаптера доступен для каждого физического сетевого адаптера на каждом сервере в кластере. Журнал производительности удаленного доступа к памяти (RDMA) доступен для каждого физического сетевого адаптера с включенным RDMA.

   > [!NOTE]
   > Не удается собрать журнал производительности для сетевых адаптеров на недоступном сервере. Коллекция будет возобновлена автоматически при резервном копировании сервера.

## <a name="series-names-and-units"></a>Имена и единицы рядов

Эти серии собираются для каждого подходящего сетевого адаптера:

| Ряд                               | Единица измерения            |
|--------------------------------------|-----------------|
| `netadapter.bandwidth.inbound`       | бит в секунду |
| `netadapter.bandwidth.outbound`      | бит в секунду |
| `netadapter.bandwidth.total`         | бит в секунду |
| `netadapter.bandwidth.rdma.inbound`  | бит в секунду |
| `netadapter.bandwidth.rdma.outbound` | бит в секунду |
| `netadapter.bandwidth.rdma.total`    | бит в секунду |

   > [!NOTE]
   > Журнал производительности сетевого адаптера записывается в **битах** в секунду, а не в байтах в секунду. Сетевой адаптер 1 10 GbE может отправлять и принимать примерно 1 000 000 000 бит = 125 000 000 байт = 1,25 ГБ в секунду на теоретическом максимальном уровне.

## <a name="how-to-interpret"></a>Как интерпретировать

| Ряд                               | Как интерпретировать                                                      |
|--------------------------------------|-----------------------------------------------------------------------|
| `netadapter.bandwidth.inbound`       | Интенсивность получения данных сетевым адаптером.                         |
| `netadapter.bandwidth.outbound`      | Интенсивность передачи данных сетевым адаптером.                             |
| `netadapter.bandwidth.total`         | Общая скорость получения или отправки данных сетевым адаптером.           |
| `netadapter.bandwidth.rdma.inbound`  | Интенсивность получения данных через RDMA сетевым адаптером.               |
| `netadapter.bandwidth.rdma.outbound` | Интенсивность передачи данных через RDMA сетевым адаптером.                   |
| `netadapter.bandwidth.rdma.total`    | Общая скорость получения или отправки данных через RDMA сетевым адаптером. |

## <a name="where-they-come-from"></a>Откуда они приходят

`bytes.*` серии собираются из счетчика производительности `Network Adapter`, установленного на сервере, где установлен сетевой адаптер, по одному экземпляру на сетевой адаптер.

| Ряд                           | Счетчик источника           |
|----------------------------------|--------------------------|
| `netadapter.bandwidth.inbound`   | 8 × `Bytes Received/sec` |
| `netadapter.bandwidth.outbound`  | 8 × `Bytes Sent/sec`     |
| `netadapter.bandwidth.total`     | 8 × `Bytes Total/sec`    |

`rdma.*` серии собираются из счетчика производительности `RDMA Activity`, установленного на сервере, где установлен сетевой адаптер, по одному экземпляру на сетевой адаптер с включенным RDMA.

| Ряд                               | Счетчик источника           |
|--------------------------------------|--------------------------|
| `netadapter.bandwidth.rdma.inbound`  | 8 × `Inbound bytes/sec`  |
| `netadapter.bandwidth.rdma.outbound` | 8 × `Outbound bytes/sec` |
| `netadapter.bandwidth.rdma.total`    | 8 × *Сумма приведенного выше*   |

   > [!NOTE]
   > Счетчики измеряются для всего интервала, а не для выборки. Например, если сетевой адаптер бездействует в течение 9 секунд, но передает 200 бит в десятую секунду, его `netadapter.bandwidth.total` записываются в среднем на 20 бит в секунду в течение этого 10-секундного интервала. Это гарантирует, что журнал производительности захватывает все действия и является надежным для шума.

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте командлет [Get-NetAdapter](https://docs.microsoft.com/powershell/module/netadapter/get-netadapter) :

```PowerShell
Get-NetAdapter <Name> | Get-ClusterPerf
```

## <a name="see-also"></a>См. также:

- [Журнал производительности для Локальные дисковые пространства](performance-history.md)
