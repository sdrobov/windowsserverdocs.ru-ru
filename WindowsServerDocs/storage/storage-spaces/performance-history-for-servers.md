---
title: Журнал производительности для серверов
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/0s/2018
Keywords: Storage Spaces Direct
ms.localizationpriority: medium
ms.openlocfilehash: 33fd62376e9769c23fc6b00eefde9a9b95eb4650
ms.sourcegitcommit: 1533d994a6ddea54ac189ceb316b7d3c074307db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "1894253"
---
# <a name="performance-history-for-servers"></a>Журнал производительности для серверов

> Применимо к: Просмотр внутренних Windows Server

Этот подраздел истории [производительности для хранения пробелы прямое](performance-history.md) подробно журнал производительности, собранные для серверов. Журнал производительности доступна для каждого сервера в кластере.

   > [!NOTE]
   > Журнал производительности не может собирать для сервера, на котором не работает. Коллекция продолжит автоматически при сервер будет восстановлена.

## <a name="series-names-and-units"></a>Имена и единиц измерения

Для каждого подходящими сервера сбора этих серии:

| Серия                           | Unit    |
|----------------------------------|---------|
| `clusternode.cpu.usage`          | Процент |
| `clusternode.cpu.usage.guest`    | Процент |
| `clusternode.cpu.usage.host`     | Процент |
| `clusternode.memory.total`       |  байт   |
| `clusternode.memory.available`   |  байт   |
| `clusternode.memory.usage`       |  байт   |
| `clusternode.memory.usage.guest` |  байт   |
| `clusternode.memory.usage.host`  |  байт   |

Кроме того, такие как диска ряда `physicaldisk.size.total` сводный для всех возможных дисков, подключенного к серверу и серии адаптера сети, таких как `networkadapter.bytes.total` сводный для всех возможных сетевых адаптеров, подключенного к серверу.

## <a name="how-to-interpret"></a>Интерпретация

| Серия                           | Интерпретация                                                      |
|----------------------------------|-----------------------------------------------------------------------|
| `clusternode.cpu.usage`          | Процент времени процессора, не является простоя.                        |
| `clusternode.cpu.usage.guest`    | Процент времени процессора, используются для запросами гостя (виртуальной машины). |
| `clusternode.cpu.usage.host`     | Процент времени процессора, используемый для размещения запросами.                    |
| `clusternode.memory.total`       | Физической памяти сервера.                              |
| `clusternode.memory.available`   | Доступная память сервера.                                   |
| `clusternode.memory.usage`       | Области (недоступно) памяти сервера.                   |
| `clusternode.memory.usage.guest` | Памяти, выделенный для запросами гостя (виртуальной машины).               |
| `clusternode.memory.usage.host`  | Объем памяти, выделенный для узла запросами.                                  |

## <a name="where-they-come-from"></a>Откуда берется из

`cpu.*` Серии полученных от счетчиков производительности в зависимости от того, включен ли Hyper-V.

Если этот параметр включен Hyper-V:

| Серия                           | Счетчик исходных данных |
|----------------------------------|----------------|
| `clusternode.cpu.usage`          | `Hyper-V Hypervisor Logical Processor` > `_Total` > `% Total Run Time`      |
| `clusternode.cpu.usage.guest`    | `Hyper-V Hypervisor Virtual Processor` > `_Total` > `% Total Run Time`      |
| `clusternode.cpu.usage.host`     | `Hyper-V Hypervisor Root Virtual Processor` > `_Total` > `% Total Run Time` |

С помощью `% Total Run Time` счетчики гарантирует, что журнал производительности атрибуты всех об использовании.

Если Hyper-V не включена:

| Серия                           | Счетчик исходных данных |
|----------------------------------|----------------|
| `clusternode.cpu.usage`          | `Processor` > `_Total` > `% Processor Time` |
| `clusternode.cpu.usage.guest`    | *нуля* |
| `clusternode.cpu.usage.host`     | *то же, что общее использование* |

Несмотря на неидеальная синхронизации `clusternode.cpu.usage` всегда `clusternode.cpu.usage.host` , а также `clusternode.cpu.usage.guest`.

Же избежать `clusternode.cpu.usage.guest` всегда является суммой `vm.cpu.usage` для всех виртуальных машин на хост-сервера.

`memory.*` Серии являются (готовится к выпуску).

  > [!NOTE]
  > Счетчики заданная в период времени, не выбрано. Например, если сервер используется в течение 9 секунд, но пики к 100% ЦП в десятой секунды его `clusternode.cpu.usage` будет записана в виде 10% в среднем этот период 10 секунд. Это гарантирует журнал производительности захватывает все действия и надежна для помех.

## <a name="usage-in-powershell"></a>Об использовании в PowerShell

Командлет [Get-работу](https://docs.microsoft.com/powershell/module/failoverclusters/get-clusternode) :

```PowerShell
Get-ClusterNode <Name> | Get-ClusterPerf
```

## <a name="see-also"></a>См. также

- [Журнал производительности для прямого пробелы хранилища](performance-history.md)
