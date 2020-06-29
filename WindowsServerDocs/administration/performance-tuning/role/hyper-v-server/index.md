---
title: Обеспечение высокой производительности серверов Hyper-V
description: Рекомендации по обеспечению высокой производительности Hyper-V
ms.prod: windows-server
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: asmahi; sandysp; jopoulso
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: 983481bb1f77e07df5fadd25ecb713d243cebd85
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85471399"
---
# <a name="performance-tuning-hyper-v-servers"></a>Обеспечение высокой производительности серверов Hyper-V


Hyper-V выполняет роль сервера виртуализации в Windows Server 2016. На серверах виртуализации можно размещать несколько виртуальных машин, которые изолированы друг от друга, но совместно используют базовые ресурсы оборудования благодаря виртуализации процессоров, памяти и устройств ввода-вывода. За счет объединения серверов на одном компьютере виртуализация может повысить эффективность использования ресурсов и электроэнергии, а также снизить расходы на эксплуатацию и обслуживанию серверов. Кроме того, виртуальные машины и интерфейсы API управления обеспечивают большую гибкость для управления ресурсами, балансировки нагрузки и подготовки систем к работе.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Терминология Hyper-V](terminology.md)

-   [Архитектура Hyper-V](architecture.md)

-   [Конфигурация сервера Hyper-V](configuration.md)

-   [Производительность процессоров Hyper-V](processor-performance.md)

-   [Производительность памяти Hyper-V](memory-performance.md)

-   [Производительность ввода-вывода хранилища Hyper-V](storage-io-performance.md)

-   [Производительность ввода-вывода сети Hyper-V](network-io-performance.md)

-   [Обнаружение узких мест в виртуализированной среде](detecting-virtualized-environment-bottlenecks.md)

-   [Виртуальные машины Linux](linux-virtual-machine-considerations.md)
