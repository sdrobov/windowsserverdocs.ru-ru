---
title: Производительность операций ввода-вывода в сети Hyper-V
description: Вопросы производительности сетевых операций ввода-вывода в настройке производительности Hyper-V
ms.prod: windows-server
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: asmahi; sandysp; jopoulso
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: dcf43bf41edada0a2e3df6fde825ff128a119a8f
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85471359"
---
# <a name="hyper-v-network-io-performance"></a>Производительность операций ввода-вывода в сети Hyper-V

Сервер 2016 содержит несколько улучшений и новых функций для оптимизации производительности сети в Hyper-V.  Документация по оптимизации производительности сети будет включена в будущую версию этой статьи.

## <a name="live-migration"></a>Динамическая миграция

Динамическая миграция позволяет прозрачно перемещать работающие виртуальные машины с одного узла отказоустойчивого кластера на другой узел в том же кластере без разрыва сетевого подключения или наблюдаемого простоя.

> [!NOTE]
> Для отказоустойчивой кластеризации требуется общее хранилище для узлов кластера.

Процесс перемещения работающей виртуальной машины можно разделить на две основные фазы. На первом этапе производится копирование памяти виртуальной машины с текущего узла на новый узел. Второй этап передает состояние виртуальной машины с текущего узла на новый узел. Длительность обоих фаз сильно зависит от скорости передачи данных с текущего узла на новый узел.

Предоставление выделенной сети для трафика динамической миграции помогает снизить время, необходимое для выполнения динамической миграции, и обеспечивает постоянную продолжительность миграции.

![Пример конфигурации динамической миграции Hyper-v](../../media/perftune-guide-live-migration.png)

Кроме того, увеличение количества буферов отправки и получения на каждом сетевом адаптере, участвующем в переносе, может повысить производительность миграции.

В Windows Server 2012 R2 появился параметр ускорения динамическая миграция путем сжатия памяти перед передачей по сети или использования удаленного прямого доступа к памяти (RDMA), если оборудование поддерживает его.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Терминология Hyper-V](terminology.md)

-   [Архитектура Hyper-V](architecture.md)

-   [Конфигурация сервера Hyper-V](configuration.md)

-   [Производительность процессоров Hyper-V](processor-performance.md)

-   [Производительность памяти Hyper-V](memory-performance.md)

-   [Производительность ввода-вывода хранилища Hyper-V](storage-io-performance.md)

-   [Обнаружение узких мест в виртуализированной среде](detecting-virtualized-environment-bottlenecks.md)

-   [Виртуальные машины Linux](linux-virtual-machine-considerations.md)
