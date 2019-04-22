---
title: Журнал производительности для серверов
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/0s/2018
Keywords: Локальные дисковые пространства
ms.localizationpriority: medium
ms.openlocfilehash: 33fd62376e9769c23fc6b00eefde9a9b95eb4650
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59820595"
---
# <a name="performance-history-for-servers"></a>Журнал производительности для серверов

> Область применения. Сборка из программы предварительной оценки Windows Server

Этот подраздел из [журнал производительности дисковых](performance-history.md) подробно описывается журнал производительности, собранных для серверов. Журнал производительности доступен для всех серверов в кластере.

   > [!NOTE]
   > Журнал производительности не собираются для сервера, не работает. Коллекция будет возобновлена автоматически, когда сервер возобновляет работу.

## <a name="series-names-and-units"></a>Имена рядов и единицы

Этих рядов собираются для всех соответствующих серверов.

| серии                           | Единица измерения    |
|----------------------------------|---------|
| `clusternode.cpu.usage`          | Процентов |
| `clusternode.cpu.usage.guest`    | Процентов |
| `clusternode.cpu.usage.host`     | Процентов |
| `clusternode.memory.total`       | байт   |
| `clusternode.memory.available`   | байт   |
| `clusternode.memory.usage`       | байт   |
| `clusternode.memory.usage.guest` | байт   |
| `clusternode.memory.usage.host`  | байт   |

Кроме того, такие как диск серии `physicaldisk.size.total` объединяются для всех соответствующих дисках, присоединенных к серверу, серии адаптера сети, такие как `networkadapter.bytes.total` объединяются для всех соответствующих сетевых адаптеров, подключенных к серверу.

## <a name="how-to-interpret"></a>Способ интерпретации

| серии                           | Способ интерпретации                                                      |
|----------------------------------|-----------------------------------------------------------------------|
| `clusternode.cpu.usage`          | Процент времени процессора, который еще не простаивает.                        |
| `clusternode.cpu.usage.guest`    | Процент времени процессора, используемый для спроса на виртуальной машине. |
| `clusternode.cpu.usage.host`     | Процент времени процессора, используемый для узла спроса.                    |
| `clusternode.memory.total`       | Общий объем физической памяти сервера.                              |
| `clusternode.memory.available`   | Свободная память сервера.                                   |
| `clusternode.memory.usage`       | Выделенную память (недоступно) сервера.                   |
| `clusternode.memory.usage.guest` | Объем памяти, выделенный виртуальной машине запросу.               |
| `clusternode.memory.usage.host`  | Объем памяти, выделенный узел требования.                                  |

## <a name="where-they-come-from"></a>Откуда они берутся

`cpu.*` Ряда собираются из разных счетчиков производительности в зависимости от того, является ли Hyper-V включен.

Если Hyper-V включен:

| серии                           | Счетчик источника |
|----------------------------------|----------------|
| `clusternode.cpu.usage`          | `Hyper-V Hypervisor Logical Processor` > `_Total` > `% Total Run Time`      |
| `clusternode.cpu.usage.guest`    | `Hyper-V Hypervisor Virtual Processor` > `_Total` > `% Total Run Time`      |
| `clusternode.cpu.usage.host`     | `Hyper-V Hypervisor Root Virtual Processor` > `_Total` > `% Total Run Time` |

С помощью `% Total Run Time` счетчики гарантирует, что журнал производительности атрибуты все сведения об использовании.

Если Hyper-V не включена:

| серии                           | Счетчик источника |
|----------------------------------|----------------|
| `clusternode.cpu.usage`          | `Processor` > `_Total` > `% Processor Time` |
| `clusternode.cpu.usage.guest`    | *ноль* |
| `clusternode.cpu.usage.host`     | *так же, как общее использование* |

Несмотря на несовершенно синхронизации `clusternode.cpu.usage` всегда `clusternode.cpu.usage.host` , а также `clusternode.cpu.usage.guest`.

С тем же механизмом `clusternode.cpu.usage.guest` всегда равно сумме `vm.cpu.usage` для всех виртуальных машин на сервере узла.

`memory.*` Рядов являются (ОЖИДАЕТСЯ в ближайшее время).

  > [!NOTE]
  > Счетчики измеряемый в течение всего интервала, не попали в выборку. Например, если сервер находится в состоянии бездействия 9 секунд, но пики на 100% ресурсов ЦП в десятой секунды его `clusternode.cpu.usage` будут записываться как 10% в среднем за этот 10-секундный интервал. Это гарантирует, что его журнал производительности записывает все действия и надежна для шума.

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте [Get-ClusterNode](https://docs.microsoft.com/powershell/module/failoverclusters/get-clusternode) командлета:

```PowerShell
Get-ClusterNode <Name> | Get-ClusterPerf
```

## <a name="see-also"></a>См. также

- [Журнал производительности для дисковых пространств](performance-history.md)
