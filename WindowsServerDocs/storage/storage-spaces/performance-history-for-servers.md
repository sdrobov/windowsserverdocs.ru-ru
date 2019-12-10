---
title: Журнал производительности для серверов
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/05/2018
Keywords: Локальные дисковые пространства
ms.localizationpriority: medium
ms.openlocfilehash: bbfc92f7926b93f5f6716514e64672f4aa304c0f
ms.sourcegitcommit: e817a130c2ed9caaddd1def1b2edac0c798a6aa2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2019
ms.locfileid: "74945251"
---
# <a name="performance-history-for-servers"></a>Журнал производительности для серверов

> Область применения: Windows Server 2019

В этом подразделе [журнала производительности для Локальные дисковые пространства](performance-history.md) подробно описывается журнал производительности, собранный для серверов. Журнал производительности доступен для каждого сервера в кластере.

   > [!NOTE]
   > Невозможно собрать журнал производительности для сервера, который не работает. Коллекция будет возобновлена автоматически при резервном копировании сервера.

## <a name="series-names-and-units"></a>Имена и единицы рядов

Эти серии собираются для каждого подходящего сервера:

| Серия                           | Unit    |
|----------------------------------|---------|
| `clusternode.cpu.usage`          | percent |
| `clusternode.cpu.usage.guest`    | percent |
| `clusternode.cpu.usage.host`     | percent |
| `clusternode.memory.total`       | байт   |
| `clusternode.memory.available`   | байт   |
| `clusternode.memory.usage`       | байт   |
| `clusternode.memory.usage.guest` | байт   |
| `clusternode.memory.usage.host`  | байт   |

Кроме того, ряды дисков, такие как `physicaldisk.size.total`, объединяются для всех подходящих дисков, подключенных к серверу, и серии сетевых адаптеров, например `networkadapter.bytes.total`, объединяются для всех подходящих сетевых адаптеров, подключенных к серверу.

## <a name="how-to-interpret"></a>Как интерпретировать

| Серия                           | Как интерпретировать                                                      |
|----------------------------------|-----------------------------------------------------------------------|
| `clusternode.cpu.usage`          | Процент времени процессора, который не находится в состоянии простоя.                        |
| `clusternode.cpu.usage.guest`    | Процент времени процессора, используемого для гостевых (виртуальных машин) потребностей. |
| `clusternode.cpu.usage.host`     | Процент времени процессора, используемого для спроса на узел.                    |
| `clusternode.memory.total`       | Общий объем физической памяти сервера.                              |
| `clusternode.memory.available`   | Объем доступной памяти сервера.                                   |
| `clusternode.memory.usage`       | Выделенный (недоступный) объем памяти сервера.                   |
| `clusternode.memory.usage.guest` | Память, выделенная для гостевого компьютера (виртуальной машины).               |
| `clusternode.memory.usage.host`  | Память, выделенная для спроса на узел.                                  |

## <a name="where-they-come-from"></a>Откуда они приходят

Серии `cpu.*` собираются из разных счетчиков производительности в зависимости от того, включена ли технология Hyper-V.

Если Hyper-V включен:

| Серия                           | Счетчик источника |
|----------------------------------|----------------|
| `clusternode.cpu.usage`          | `Hyper-V Hypervisor Logical Processor` > `_Total` > `% Total Run Time`      |
| `clusternode.cpu.usage.guest`    | `Hyper-V Hypervisor Virtual Processor` > `_Total` > `% Total Run Time`      |
| `clusternode.cpu.usage.host`     | `Hyper-V Hypervisor Root Virtual Processor` > `_Total` > `% Total Run Time` |

Использование счетчиков `% Total Run Time` гарантирует, что все атрибуты журнала производительности используются.

Если Hyper-V не включен:

| Серия                           | Счетчик источника |
|----------------------------------|----------------|
| `clusternode.cpu.usage`          | `Processor` > `_Total` > `% Processor Time` |
| `clusternode.cpu.usage.guest`    | *нуль* |
| `clusternode.cpu.usage.host`     | *аналогично общему использованию* |

Несмотря на синхронизацию неидеальны, `clusternode.cpu.usage` всегда `clusternode.cpu.usage.host` плюс `clusternode.cpu.usage.guest`.

С той же оговоркой `clusternode.cpu.usage.guest` всегда является суммой `vm.cpu.usage` для всех виртуальных машин на сервере узла.

Серии `memory.*` (ожидается в ближайшее время).

  > [!NOTE]
  > Счетчики измеряются для всего интервала, а не для выборки. Например, если сервер бездействует в течение 9 секунд, но пики 100% ЦП в десятой секунде, его `clusternode.cpu.usage` будет записано в среднем на 10% в течение этого 10-секундного интервала. Это гарантирует, что журнал производительности захватывает все действия и является надежным для шума.

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте командлет [Get-ClusterNode](https://docs.microsoft.com/powershell/module/failoverclusters/get-clusternode) :

```PowerShell
Get-ClusterNode <Name> | Get-ClusterPerf
```

## <a name="see-also"></a>См. также

- [Журнал производительности для Локальные дисковые пространства](performance-history.md)
