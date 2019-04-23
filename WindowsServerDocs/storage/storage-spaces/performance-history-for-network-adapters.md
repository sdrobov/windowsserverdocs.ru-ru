---
title: Журнал производительности сетевого адаптера
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
Keywords: Локальные дисковые пространства
ms.localizationpriority: medium
ms.openlocfilehash: 340999a8f440975d3736277b1a30dddbb942785d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59849985"
---
# <a name="performance-history-for-network-adapters"></a>Журнал производительности сетевого адаптера

> Область применения. Сборка из программы предварительной оценки Windows Server

Этот подраздел из [журнал производительности дисковых](performance-history.md) подробно описывается журнал производительности, собранных для сетевых адаптеров. Журнал производительности сетевого адаптера доступна для каждого физического сетевого адаптера на каждом сервере в кластере. Удаленный доступ к памяти (RDMA) доступен журнал производительности для каждого физического сетевого адаптера с поддержкой RDMA.

   > [!NOTE]
   > Журнал производительности не могут быть собраны для сетевых адаптеров на сервере, который не работает. Коллекция будет возобновлена автоматически, когда сервер возобновляет работу.

## <a name="series-names-and-units"></a>Имена рядов и единицы

Этих рядов собираются для каждого адаптера сети:

| серии                               | Единица измерения            |
|--------------------------------------|-----------------|
| `netadapter.bandwidth.inbound`       | Бит в секунду |
| `netadapter.bandwidth.outbound`      | Бит в секунду |
| `netadapter.bandwidth.total`         | Бит в секунду |
| `netadapter.bandwidth.rdma.inbound`  | Бит в секунду |
| `netadapter.bandwidth.rdma.outbound` | Бит в секунду |
| `netadapter.bandwidth.rdma.total`    | Бит в секунду |

   > [!NOTE]
   > Журнал производительности сетевого адаптера регистрируется в **bits** в секунду, а не в байтах в секунду. Один сетевой адаптер 10 GbE может отправлять и получать примерно 1 000 000 000 бит = 125,000,000 байт = 1,25 ГБ в секунду до теоретического максимума.

## <a name="how-to-interpret"></a>Способ интерпретации

| серии                               | Способ интерпретации                                                      |
|--------------------------------------|-----------------------------------------------------------------------|
| `netadapter.bandwidth.inbound`       | Интенсивность данные, полученные сетевым адаптером.                         |
| `netadapter.bandwidth.outbound`      | Скорость обмена данными по сетевому адаптеру.                             |
| `netadapter.bandwidth.total`         | Общая частота данных получено или отправлено сетевым адаптером.           |
| `netadapter.bandwidth.rdma.inbound`  | Интенсивность данные, полученные через RDMA сетевым адаптером.               |
| `netadapter.bandwidth.rdma.outbound` | Скорость обмена данными через RDMA по сетевому адаптеру.                   |
| `netadapter.bandwidth.rdma.total`    | Общая частота данных получено или отправлено через RDMA сетевым адаптером. |

## <a name="where-they-come-from"></a>Откуда они берутся

`bytes.*` Ряда собираются из `Network Adapter` счетчика производительности установки на сервере, где установлен сетевой адаптер, по одному экземпляру каждого сетевого адаптера.

| серии                           | Счетчик источника           |
|----------------------------------|--------------------------|
| `netadapter.bandwidth.inbound`   | 8 × `Bytes Received/sec` |
| `netadapter.bandwidth.outbound`  | 8 × `Bytes Sent/sec`     |
| `netadapter.bandwidth.total`     | 8 × `Bytes Total/sec`    |

`rdma.*` Ряда собираются из `RDMA Activity` счетчика производительности установки на сервере, где установлен сетевой адаптер, по одному экземпляру каждого сетевого адаптера с поддержкой RDMA.

| серии                               | Счетчик источника           |
|--------------------------------------|--------------------------|
| `netadapter.bandwidth.rdma.inbound`  | 8 × `Inbound bytes/sec`  |
| `netadapter.bandwidth.rdma.outbound` | 8 × `Outbound bytes/sec` |
| `netadapter.bandwidth.rdma.total`    | 8 × *сумму указанных выше*   |

   > [!NOTE]
   > Счетчики измеряемый в течение всего интервала, не попали в выборку. Например, если сетевой адаптер находится в состоянии бездействия 9 секунд, но передача 200 бит в десятой секунды его `netadapter.bandwidth.total` будут записываться как 20 бит в секунду в среднем за этот 10-секундный интервал. Это гарантирует, что его журнал производительности записывает все действия и надежна для шума.

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте [Get-NetAdapter](https://docs.microsoft.com/powershell/module/netadapter/get-netadapter) командлета:

```PowerShell
Get-NetAdapter <Name> | Get-ClusterPerf
```

## <a name="see-also"></a>См. также

- [Журнал производительности для дисковых пространств](performance-history.md)
