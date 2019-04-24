---
title: Обеспечение высокой производительности серверов Hyper-V
description: Рекомендации по обеспечению высокой производительности Hyper-V
ms.prod: windows-server-threshold
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: Asmahi; SandySp; JoPoulso
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: 0d850ba198d269888dfa0ad323546541983b88e1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59891755"
---
# <a name="performance-tuning-hyper-v-servers"></a>Обеспечение высокой производительности серверов Hyper-V


Hyper-V выполняет роль сервера виртуализации в Windows Server 2016. На серверах виртуализации можно размещать несколько виртуальных машин, которые изолированы друг от друга, но совместно используют базовые ресурсы оборудования благодаря виртуализации процессоров, памяти и устройств ввода-вывода. За счет объединения серверов на одном компьютере виртуализация может повысить эффективность использования ресурсов и электроэнергии, а также снизить расходы на эксплуатацию и обслуживанию серверов. Кроме того, виртуальные машины и интерфейсы API управления обеспечивают большую гибкость для управления ресурсами, балансировки нагрузки и подготовки систем к работе.

## <a name="see-also"></a>См. также

-   [Терминология Hyper-V](terminology.md)

-   [Архитектура Hyper-V](architecture.md)

-   [Конфигурация сервера Hyper-V](configuration.md)

-   [Производительность процессоров Hyper-V](processor-performance.md)

-   [Производительность памяти Hyper-V](memory-performance.md)

-   [Производительность ввода-вывода хранилища Hyper-V](storage-io-performance.md)

-   [Производительность ввода-вывода сети Hyper-V](network-io-performance.md)

-   [Обнаружение узких мест в виртуализированной среде](detecting-virtualized-environment-bottlenecks.md)

-   [Виртуальные машины Linux](linux-virtual-machine-considerations.md)
