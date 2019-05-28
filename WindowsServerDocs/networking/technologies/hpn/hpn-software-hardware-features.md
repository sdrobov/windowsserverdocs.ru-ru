---
title: Программно и аппаратно интегрируемые компоненты и технологии
description: Эти функции имеют компоненты программного обеспечения и оборудования. Программное обеспечение тесно связан с аппаратных возможностей, которые требуются для работы функции. Примеры этих вызовов включают VMMQ, VMQ, отправляющей стороны IPv4 контрольной суммы Tcpv4 и RSS.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 0cafb1cc-5798-42f5-89b6-3ffe7ac024ba
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/12/2018
ms.openlocfilehash: a58d1e14dc8f543f25ef241f2a65054599136031
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817395"
---
# <a name="software-and-hardware-sh-integrated-features-and-technologies"></a>Программно и аппаратно интегрируемые компоненты и технологии

Эти функции имеют компоненты программного обеспечения и оборудования. Программное обеспечение тесно связан с аппаратных возможностей, которые требуются для работы функции. Примеры этих вызовов включают VMMQ, VMQ, отправляющей стороны IPv4 контрольной суммы Tcpv4 и RSS.

>[!TIP]
>SH и HO функции доступны в том случае, если установленный сетевой Адаптер поддерживает его. С описанием функций мы рассмотрим, как определить, поддерживает ли ваша сетевая КАРТА функцию.

## <a name="converged-nic"></a>Сетевой Адаптер со схождением 

Сетевой Адаптер со схождением является это технология, позволяющая виртуальных сетевых адаптеров на узле Hyper-V, чтобы предоставлять службы RDMA для хост-процессы. Windows Server 2016 больше не требуется отдельные сетевые адаптеры для RDMA. Функция поддержки групп Сетевых со схождением позволяет виртуальных сетевых адаптеров в раздела узла (Vnic) для предоставления RDMA к разделу узла и совместно использовать пропускную способность для сетевых адаптеров между RDMA и виртуальной Машины и другого трафика TCP/UDP в виде справедливого и управляемой.

![Конвергентную сетевую КАРТУ с помощью SDN](../../media/Converged-NIC/conv-nic-sdn.png)

Вы можете управлять со схождением операцию сетевой Адаптер с помощью VMM или Windows PowerShell. Командлеты PowerShell являются те же командлеты, используемые для RDMA (см. ниже).

Для использования со схождением возможности сетевого Адаптера:

1.  Убедитесь, что установить узлов для использования DCB.

2.  Убедитесь, чтобы включить RDMA в сетевой КАРТЕ, или в случае в команде SET, привязываются сетевые карты к коммутатору Hyper-V. 

3.  Убедитесь, что включить RDMA на виртуальных сетевых адаптеров, предназначенные для RDMA на узле. 

Дополнительные сведения о RDMA и SET, см. в разделе [удаленный доступ к памяти (RDMA) и коммутатора внедренных коммутаторов (SET)](https://docs.microsoft.com/windows-server/virtualization/hyper-v-virtual-switch/rdma-and-switch-embedded-teaming).

## <a name="data-center-bridging-dcb"></a>Мост для центра обработки данных 

DCB — это набор стандартов Institute of Electrical и Electronics инженеров IEEE, включающих Конвергентные в центрах обработки данных. DCB обеспечивает управление пропускной способности на основе очередей оборудования в основном приложении с поддержкой соседний коммутатор. Весь трафик для хранения данных к сети кластера межпроцессное взаимодействие (IPC) и управления совместно использовать сетевую инфраструктуру Ethernet. В Windows Server 2016 DCB может применяться к любой сетевой платы по отдельности, а к сетевым адаптерам, привязанного к Hyper-V переключения.

Windows Server использует мост центра обработки данных, на основании приоритета потока управления (PFC), стандартизированный в IEEE 802.1Qbb. PFC создает (почти) без потерь сетевую структуру, Предотвращение переполнения в классы трафика. Windows Server также использует расширенный передачи выбора (ETS), стандартизированный в IEEE 802.1Qaz. ETS позволяет деления пропускной способности в части, зарезервированный для до восьми классы трафика. Каждый класс трафика имеет свой собственный передачи в очередь и, при помощи PFC, можно запускать и останавливать передачи в пределах класса.

Дополнительные сведения см. в разделе [Data Center Bridging (DCB)](https://docs.microsoft.com/windows-server/networking/technologies/dcb/dcb-top).

## <a name="hyper-v-network-virtualization"></a>Виртуализация сети Hyper-V

| | |
|---|---|
| **V1 (HNVv1)**             | Представленный в Windows Server 2012, виртуализации сети Hyper-V (HNV) обеспечивает виртуализацию сетей клиентов на основе общего, физической сетевой инфраструктуры. С минимальными изменениями, необходимых на физической сетевой инфраструктуре, HNV дают поставщикам услуг необходимую гибкость для развертывания и перехода клиентских рабочих нагрузок в любом месте в трех облаках: облако поставщика службы, частное облако или общедоступное облако Microsoft Azure.                                         |
| **v2 NVGRE (HNVv2 NVGRE)** | В Windows Server 2016 и System Center Virtual Machine Manager Microsoft предоставляет решение виртуализации сети end-to-end, включающий шлюз RAS, балансировка нагрузки программного обеспечения, сетевого контроллера и многое другое. Дополнительные сведения см. в разделе [обзор виртуализации сети Hyper-V в Windows Server 2016](https://technet.microsoft.com/windows-server-docs/networking/sdn/technologies/hyper-v-network-virtualization/hyperv-network-virtualization-overview-windows-server). |
| **VxLAN v2 (HNVv2 VxLAN)** | В Windows Server 2016 является частью SDN — расширение, которое можно управлять с помощью сетевого контроллера.    |
---

## <a name="ipsec-task-offload-ipsecto"></a>Разгрузка задач IPsec (IPsecTO) 

Разгрузку задач IPsec — это функция сетевой Адаптер, который позволяет операционной системе для использования процессора на сетевой Адаптер для работы шифрования IPsec.

>[!IMPORTANT] 
>Разгрузка задач IPsec — это устаревшая технология, которая не поддерживается в большинстве сетевых адаптеров, и где он существует, она отключена по умолчанию.

## <a name="private-virtual-local-area-network-pvlan"></a>Частной виртуальной локальной сети (PVLAN). 

Pvlan разрешать подключения только между виртуальными машинами на одном сервере виртуализации. Частная виртуальная сеть не привязан к физическому сетевому адаптеру. Частная виртуальная сеть изолирована от всего внешнего сетевого трафика на сервере виртуализации, а также любой сетевой трафик между операционной системы и внешней сетью. Сеть этого типа полезна, если нужно создать изолированную сетевую среду, например изолированный тестовый домен. Hyper-V и стеки SDN поддерживает только режим порта изолированный режим PVLAN.

Дополнительные сведения об изоляции PVLAN см. в разделе [System Center: Блог инженеров Virtual Machine Manager](https://blogs.technet.microsoft.com/scvmm/2013/06/04/logical-networks-part-iv-pvlan-isolation/).

## <a name="remote-direct-memory-access-rdma"></a>Удаленный доступ к памяти (RDMA) 

RDMA — это сетевые технология, которая обеспечивает обмен данными высокой пропускной способностью и малой задержкой, которая сводит к минимуму использование ЦП. RDMA поддерживает копирования сети путем включения сетевого адаптера для передачи данных непосредственно в или из памяти приложения. С поддержкой RDMA означает, что сетевой Адаптер (физический или виртуальный) способен обеспечить все многообразие RDMA клиенту RDMA. С другой стороны, обеспечивающими, означает, что подвергает сетевую КАРТУ с поддержкой RDMA интерфейс RDMA вверх по стеку.

Дополнительные сведения о RDMA, см. в разделе [удаленный доступ к памяти (RDMA) и коммутатора внедренных коммутаторов (SET)](https://docs.microsoft.com/windows-server/virtualization/hyper-v-virtual-switch/rdma-and-switch-embedded-teaming).

## <a name="receive-side-scaling-rss"></a>Receive Side Scaling (RSS) 

RSS — это функция сетевой Адаптер, отделяющее разные наборы потоков и размещает их на разные процессоры для обработки. RSS распараллеливание обработки, что позволяет ведущему приложению масштабироваться до очень высокой скорости сетевого подключения. 

Дополнительные сведения см. в разделе [на стороне приема масштабирование (RSS)](https://docs.microsoft.com/windows-hardware/drivers/network/introduction-to-receive-side-scaling).

## <a name="single-root-input-output-virtualization-sr-iov"></a>Виртуализация ввода вывода с единым корнем (SR-IOV) 

SR-IOV позволяет трафика виртуальных Машин для перемещения непосредственно из сетевой КАРТЫ к виртуальной Машине без передачи через узел Hyper-V. SR-IOV — это Невероятная улучшение производительности для виртуальной Машины, но не имеет возможности для узла для управления этому каналу. Используйте только SR-IOV, когда рабочая нагрузка хорошо работающие доверенной и обычно единственной виртуальной Машиной на узле.

Трафик, который использует SR-IOV обходит коммутатор Hyper-V, это означает, что все политики, например, списки управления доступом, или не будет применяться управление пропускной способностью. Трафик SR-IOV также могут передаваться через любой возможности виртуализации сети, поэтому NV GRE или VxLAN инкапсуляция не может использоваться. Использование SR-IOV только хорошо доверенные рабочие нагрузки в определенных ситуациях. Кроме того нельзя использовать политиками узла размещения, управление пропускной способностью и технологии виртуализации.

В будущем SR-IOV позволяет две технологии: Универсальный потока таблиц (GFT) и оборудование разгрузки качества обслуживания (Управление пропускной способностью в сетевом Интерфейсе) — после их поддержки сетевых адаптеров в нашей экосистеме. Сочетание этих двух технологий сделает полезные для всех виртуальных машин, SR-IOV позволяет политики, виртуализации и применение правил управления пропускной способности и может результат в отличный оставляющим перенаправление в целом приложения SR-iov.

Дополнительные сведения см. в разделе [Обзор из одной корневой виртуализации ввода-вывода (SR-IOV)](https://docs.microsoft.com/windows-hardware/drivers/network/overview-of-single-root-i-o-virtualization--sr-iov-).

## <a name="tcp-chimney-offload"></a>Разгрузка TCP Chimney

Разгрузка TCP Chimney, также известный как TCP разгрузки TCP/IP (TOE), — это технология, позволяющую узлу для разгрузки все TCP обработки к сетевому адаптеру. Так как стек TCP в Windows Server почти всегда является более эффективным, чем подсистема TOE, использование разгрузки TCP Chimney не рекомендуется.

>[!IMPORTANT]
>Разгрузка TCP Chimney — это технология, не рекомендуется. Мы рекомендуем не использовать разгрузки TCP Chimney как Майкрософт может прекратить поддерживать его в будущем.

## <a name="virtual-local-area-network-vlan"></a>Виртуальной локальной сети (VLAN) 

Виртуальная ЛС имеет расширение заголовок кадра Ethernet, чтобы включить секционирование из локальной сети в нескольких виртуальных локальных сетей, используя свое собственное адресное пространство. В Windows Server 2016 виртуальные ЛС задаются на портах коммутатора Hyper-V, или установив групповые интерфейсы в командах, объединение Сетевых карт. Дополнительные сведения см. в разделе [объединение Сетевых карт и виртуальные локальные сети (VLAN)](https://docs.microsoft.com/windows-server/networking/technologies/nic-teaming/nict-and-vlans).

## <a name="virtual-machine-queue-vmq"></a>с очередью виртуальной машины (VMQ). 

Vmq — это функция сетевой Адаптер, который выделяет очереди для каждой виртуальной Машины. Каждый раз, когда у вас есть Hyper-V включена; необходимо также включить VMQ. В Windows Server 2016 Vmq используйте виртуальных портов коммутатора сетевого Адаптера с одной очередью, назначенные vPort, чтобы указать те же функциональные возможности. Дополнительные сведения см. в разделе [виртуального масштабирования на стороне приема (vRSS)](https://docs.microsoft.com/windows-server/networking/technologies/vrss/vrss-top) и [объединение Сетевых карт](https://docs.microsoft.com/windows-server/networking/technologies/nic-teaming/nic-teaming).

## <a name="virtual-machine-multi-queue-vmmq"></a>Виртуальную машину с несколькими очередями (VMMQ) 

VMMQ — это функция сетевой КАРТЫ, которое разрешает трафик для виртуальной Машины для распределения по нескольким очередям каждый обрабатывается другой физический процессор. Трафик передается несколько LPs на виртуальной Машине, как было бы в vRSS, что позволяет по доставке значительной пропускной способности сети для виртуальной Машины.

---