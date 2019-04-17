---
title: Новые возможности виртуализации сети Hyper-V в Windows Server 2016
description: В этом разделе содержатся сведения о новых возможностях виртуализации сети Hyper-V в Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0254275a-0a77-40a9-b68a-1029284c03fe
ms.author: pashort
author: shortpatti
ms.date: 03/19/2018
ms.openlocfilehash: 0954768944e44848debfbb7fb752a13ca47031c2
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="whats-new-in-hyper-v-network-virtualization-in-windows-server-2016"></a>Новые возможности виртуализации сети Hyper-V в Windows Server 2016

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе описываются функции виртуализации сети Hyper-V (HNV), добавленные или измененные в Windows Server 2016.  
  
## <a name="BKMK_IPAM2012R2"></a>Обновления в виртуализации сети  
HNV предоставляет расширенную поддержку в следующих областях:  
  
|Функции и функциональные возможности|Новые и совершенствуют существующие|Описание|  
|--------------------------|-------------------|---------------|  
|[Программируемый коммутатора Hyper-V](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#SDN)|Новые функции|Политики HNV программировать через сетевой контроллер корпорации Майкрософт.|  
|[Поддержка инкапсуляция VXLAN](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#VXLAN)|Новые функции|HNV теперь поддерживает инкапсуляция VXLAN.|  
|[Совместимость программного обеспечения балансировки нагрузки (SLB)](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#SLB)|Новые функции|HNV полностью интегрированы с подсистемой балансировки нагрузки программного обеспечения корпорации Майкрософт.|  
|[Совместимые IEEE Ethernet заголовки](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#L2)|Улучшена|Соответствует стандартам IEEE Ethernet|  
  
### <a name="SDN"></a>Программируемый коммутатора Hyper-V  
HNV является основным компонентом обновленные решения программно-конфигурируемые сети (SDN) корпорации Майкрософт и полностью интегрированы в стек SDN.  
  
Сетевой контроллер корпорации Майкрософт для нового помещает политики HNV вниз, чтобы агент узла под управлением на каждом узле, с помощью открыть виртуальный коммутатор протокола управления базы данных (OVSDB) как Южный интерфейса (SBI). Агент узла хранится эта политика, с помощью настройки из [схемы VTEP](https://github.com/openvswitch/ovs/blob/master/vtep/vtep.ovsschema) и программы правила потока обработки сложных в подсистемы обработки потока производительное коммутатора Hyper-V.  
  
Модуль поток внутри коммутатора Hyper-V — тот же механизм, используемый в Microsoft Azure&trade;, который оказалось в крупномасштабных в общедоступном облаке Microsoft Azure. Кроме того целый стек SDN вверх через сетевой контроллер и поставщике сетевых ресурсов (подробности станут известны скоро) согласуется с Microsoft Azure, таким образом перенос питания общедоступное облако Microsoft Azure на наших предприятия и клиентам поставщика услуг размещения.  
  
> [!NOTE]  
> Дополнительные сведения о OVSDB см. в разделе [RFC 7047](http://www.rfc-editor.org/info/rfc7047).  
  
Коммутатор Hyper-V поддерживает оба правила без учета и с отслеживанием состояния потока, исходя из простого поиска «действие» в корпорации Майкрософт подсистемы обработки потока.  
 
![Windows Server 2016 Hyper-V коммутатора](../../../media/what-s-new-in-hyper-v-network-virtualization-in-windows-server/HNVOverview.png)  
  
### <a name="VXLAN"></a>Поддержка инкапсуляция VXLAN  
Виртуальные расширяемые локальной сети (VXLAN - [RFC 7348](http://www.rfc-editor.org/info/rfc7348)) протокола широкое распространение на рынке с поддержкой из поставщиков, таких как Cisco, Brocade, Dell, HP и другие. Виртуализация теперь также поддерживает эту схему инкапсуляции режиме MAC распространения через сетевой контроллер Майкрософт для сопоставления программ для клиента наложения сети IP-адреса (адреса клиента или ЦС) на underlay физической сети IP-адреса (адрес поставщика или АП). NVGRE и VXLAN разгрузку задач поддерживаются для повышения производительности через сторонние драйверы.  
  
### <a name="SLB"></a>Совместимость программного обеспечения балансировки нагрузки (SLB)  
Windows Server 2016 включает программного балансировщика нагрузки (SLB) с полной поддержки для виртуального сетевого трафика и легкое взаимодействие с HNV. SLB развернутые с помощью подсистемы обработки потока производительное v коммутатора плоскости данных и управляются сетевой контроллер виртуальных IP-адресов (VIP) или динамические сопоставления IP (DIP).  
  
### <a name="L2"></a>Совместимые IEEE Ethernet заголовки  
HNV реализует правильный заголовки L2 Ethernet, чтобы обеспечить взаимодействие с виртуальными и физическими устройств сторонних производителей, зависящие от стандартных протоколов. Microsoft, гарантирует все пакеты, передаваемые совместимые значения во всех полях, чтобы обеспечить это взаимодействие. Кроме того поддержка кадры крупного размера (данных MTU > 1780) в физической сети L2 будет необходимых для учетной записи для пакетов, расходы введенный протоколы encapsulation (NVGRE, VXLAN) гарантированной гостевых виртуальных машин, подключенных к виртуальной сети HNV Ведение 1514 MTU.  
  
## <a name="see-also"></a>См. также:  
  
-   [Обзор виртуализации сети Hyper-V](hyperv-network-virtualization-overview-windows-server.md)  
  
-   [Техническое описание виртуализации сетей Hyper-V](hyperv-network-virtualization-technical-details-windows-server.md)  
  
-   [Программно-конфигурируемой сети](../../Software-Defined-Networking--SDN-.md)  
  