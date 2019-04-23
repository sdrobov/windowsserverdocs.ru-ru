---
title: Соображения относительно виртуальной машины Linux
description: Виртуальной машины Linux и BSD
ms.prod: windows-server-threshold
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: Asmahi; SandySp; JoPoulso
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: cc6aab7825754579269eb05e591ca2a3cf5a561b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59869685"
---
# <a name="linux-virtual-machine-considerations"></a>Соображения относительно виртуальной машины Linux

BSD виртуальные машины Linux и имеют свои особенности, по сравнению с виртуальными машинами Windows в Hyper-V.

Прежде всего — присутствуют ли службы Integration Services или если виртуальная машина запущена на эмулируемым оборудованием с не просвещения. Таблица выпусков Linux и BSD, встроенными или загружаемые службы Integration Services доступна в [виртуальных машин поддерживается Linux и FreeBSD для Hyper-V в Windows](https://technet.microsoft.com/windows-server-docs/compute/hyper-v/supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows). Эти страницы имеют сетки доступных функций Hyper-V, доступных для распространения выпусков Linux и заметки на тех функциях, там, где это применимо.

Даже в том случае, если гостевой ОС выполняется служб Integration Services, его можно настроить с помощью устаревшее оборудование, который не обеспечивает наилучшую производительность. Например настройки и использования виртуального адаптера ethernet для гостей, вместо того чтобы использовать устаревший сетевой адаптер. С Windows Server 2016 расширенные сетевые, такие как SR-IOV, а также доступны.

## <a name="linux-network-performance"></a>Производительность сети для Linux

Linux по умолчанию включает аппаратное ускорение и перераспределяет нагрузку по умолчанию. Если vRSS включается в свойствах сетевого адаптера на узле и гостевой виртуальной машины Linux имеет возможность использовать vRSS возможность будет включена. В Powershell этот же параметр можно изменить с помощью `EnableNetAdapterRSS` команды.

Аналогичным образом, можно включить функцию VMMQ (RSS виртуального коммутатора) на физический сетевой Адаптер, используемый гостевой **свойства** > **Настройка...**   >  **Дополнительно** вкладке > задать **виртуального коммутатора RSS** для **включено** или включить VMMQ в Powershell, используя следующие:

```PowerShell
 Set-VMNetworkAdapter -VMName **$VMName** -VmmqEnabled $True
 ```

В гостевой дополнительная настройка TCP может выполняться путем увеличения ограничения. Для повышения производительности распространения рабочей нагрузки на нескольких процессорах и для рабочих нагрузок глубокого создает оптимальную пропускную способность, как виртуализированных рабочих нагрузок будут выполняться дольше, чем «исходного состояния системы» объектам.

Некоторые пример настройки параметров, которые были полезны в сети тесты включают:

```PowerShell
net.core.netdev_max_backlog = 30000
net.core.rmem_max = 67108864
net.core.wmem_max = 67108864
net.ipv4.tcp_wmem = 4096 12582912 33554432
net.ipv4.tcp_rmem = 4096 12582912 33554432
net.ipv4.tcp_max_syn_backlog = 80960
net.ipv4.tcp_slow_start_after_idle = 0
net.ipv4.tcp_tw_reuse = 1
net.ipv4.ip_local_port_range = 10240 65535
net.ipv4.tcp_abort_on_overflow = 1
```

Это полезное средство для микротестами сети является ntttcp, которая доступна в Windows и Linux. Версии Linux имеет открытый исходный код и доступны из [ntttcp-for-linux, на сайте github.com](https://github.com/Microsoft/ntttcp-for-linux). Версии Windows можно найти в [центра загрузки](https://gallery.technet.microsoft.com/NTttcp-Version-528-Now-f8b12769). При настройке рабочей нагрузки рекомендуется использовать столько потоков при необходимости, чтобы получить оптимальную пропускную способность. С помощью ntttcp для трафика модели `-P` параметр задает число параллельных соединений, используемых.

## <a name="linux-storage-performance"></a>Производительность хранилища Linux

Некоторые рекомендации, как показано ниже, перечислены на [советы и рекомендации по под управлением Linux в Hyper-V](https://technet.microsoft.com/windows-server-docs/compute/hyper-v/best-practices-for-running-linux-on-hyper-v). Ядро Linux имеет различные планировщики операций ввода-вывода, чтобы изменить порядок запросов с помощью различных алгоритмов. NOOP является первым обслужен очередь, передает расписание принять решение о низкоуровневой оболочкой. Рекомендуется использовать как планировщик NOOP, при запуске виртуальной машины Linux на Hyper-V. Чтобы изменить планировщик для конкретного устройства, в начальной загрузки configuration (/ etc/grub.conf, например), добавьте `elevator=noop` для параметры ядра, а затем перезапустить.

Как и в сети, максимально эффективное использование нескольких очередей с достаточно глубиной, чтобы обеспечить работоспособность узла занят преимущества производительности гостевых систем Linux с хранилищем. Производительность хранилища Microbenchmarking, вероятно, лучше всего с помощью средства тестирования fio с ядром libaio.

## <a name="see-also"></a>См. также

-   [Терминологии Hyper-V](terminology.md)

-   [Архитектура Hyper-V](architecture.md)

-   [Конфигурация сервера Hyper-V](configuration.md)

-   [Производительность процессора Hyper-V](processor-performance.md)

-   [Производительность памяти Hyper-V](memory-performance.md)

-   [Хранилище Hyper-V производительность ввода-вывода](storage-io-performance.md)

-   [Сети Hyper-V производительность ввода-вывода](network-io-performance.md)

-   [Обнаружение узких мест в виртуализованной среде](detecting-virtualized-environment-bottlenecks.md)
