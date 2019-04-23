---
title: Новые возможности виртуализации сети Hyper-V в Windows Server 2016
description: Этот раздел содержит сведения о новых возможностях виртуализации сети Hyper-V в Windows Server 2016
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
ms.openlocfilehash: 24ec9e52be3acdfced35eae4fb5f98f16d8e18f7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59837955"
---
# <a name="whats-new-in-hyper-v-network-virtualization-in-windows-server-2016"></a>Новые возможности виртуализации сети Hyper-V в Windows Server 2016

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе описываются возможности виртуализации сети Hyper-V (HNV), которые являются новыми или измененными в Windows Server 2016.  
  
## <a name="BKMK_IPAM2012R2"></a>Обновления в виртуализации сети  
HNV обеспечивает расширенную поддержку в следующих областях:  
  
|Компонент или функциональная возможность|Новая или улучшенная|Описание|  
|--------------------------|-------------------|---------------|  
|[Программируемые коммутатора Hyper-V](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#SDN)|Оператор new|Политики HNV можно программировать через сетевой контроллер Майкрософт.|  
|[Поддержка инкапсуляция VXLAN](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#VXLAN)|Оператор new|Hyper-v теперь поддерживает инкапсуляцию VXLAN.|  
|[Взаимодействие программного обеспечения подсистемы балансировки нагрузки (SLB)](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#SLB)|Оператор new|HNV полностью интегрировано с подсистемой балансировки нагрузки программного обеспечения Майкрософт.|  
|[Совместимые IEEE Ethernet заголовки](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#L2)|Улучшенная|Стандартам IEEE Ethernet|  
  
### <a name="SDN"></a>Программируемые коммутатора Hyper-V  
HNV является основным строительным блоком обновленные программно определяемой сети (SDN) в решении Майкрософт, а также полностью интегрированы в стек SDN.  
  
Новый сетевой контроллер Майкрософт помещает политики HNV вниз, чтобы агент узла под управлением на каждом узле, с помощью Open коммутатор vSwitch протокола управления базы данных (OVSDB) как южного интерфейс (SBI). Агент узла хранит эту политику, с помощью настройки из [VTEP схемы](https://github.com/openvswitch/ovs/blob/master/vtep/vtep.ovsschema) и программы правила сложного потока в высокопроизводительных подсистема обработки потока в коммутаторе Hyper-V.  
  
Подсистема обработки потока внутри коммутатора Hyper-V — это тот же механизм, используемый в Microsoft Azure&trade;, которой было доказано любого масштаба, в общедоступном облаке Microsoft Azure. Кроме того совместимых с Microsoft Azure, таким образом привнесения общедоступного облака Microsoft Azure enterprise и служба размещения весь стек SDN вверх через сетевой контроллер и поставщик сетевых ресурсов (сведения о ожидается в ближайшее время) Клиенты поставщика.  
  
> [!NOTE]  
> Дополнительные сведения о OVSDB, см. в разделе [RFC 7047](https://www.rfc-editor.org/info/rfc7047).  
  
Коммутатор Hyper-V поддерживает оба правила с отслеживанием и без отслеживания состояния потока, исходя из простого поиска «действие» в корпорации Майкрософт подсистема обработки потока.  
 
![Windows Server 2016 Hyper-V коммутатора](../../../media/what-s-new-in-hyper-v-network-virtualization-in-windows-server/HNVOverview.png)  
  
### <a name="VXLAN"></a>Поддержка инкапсуляция VXLAN  
Виртуальные расширяемые локальной сети (VXLAN - [RFC 7348](https://www.rfc-editor.org/info/rfc7348)) протокола широко используется на рынке с поддержкой от поставщиков, таких как Cisco, Brocade, Dell, HP и другим пользователям. Hyper-v теперь также поддерживает эта схема инкапсуляция с использованием режима распределения MAC через сетевой контроллер Майкрософт для программы сопоставления для клиента наложения сети IP-адресов (адрес заказчика или ЦС) на лежащие физической сети IP-адреса (поставщик Адрес или PA). Как NVGRE, так и VXLAN разгружает задач поддерживаются для повышения производительности через сторонних драйверов.  
  
### <a name="SLB"></a>Взаимодействие программного обеспечения подсистемы балансировки нагрузки (SLB)  
Windows Server 2016 включает подсистему балансировки нагрузки (SLB) с полной поддержкой трафика виртуальной сети и беспрепятственного взаимодействия с HNV. Реализуется через подсистему обработки потока высокопроизводительных v коммутатора плоскости данных и управляется сетевым контроллером, виртуальный IP-адрес (VIP) / динамический SLB сопоставления IP-адрес (DIP).  
  
### <a name="L2"></a>Совместимые IEEE Ethernet заголовки  
HNV реализует правильные заголовки L2 Ethernet, чтобы обеспечить взаимодействие с использованием сторонних виртуальных и физических устройств, которые зависят от стандартных протоколов. Microsoft, гарантирует все передаваемые пакеты совместимые значения во всех полях для этого взаимодействия. Кроме того, поддержка большие кадры (данных MTU > 1780) в физической сети L2 требуется учетная запись для пакета, издержки, вызванные протоколы encapsulation (NVGRE, VXLAN) гарантией того, гостевые виртуальные машины, подключенные к виртуальной сети HNV Ведение 1514 MTU.  
  
## <a name="see-also"></a>См. также  
  
-   [Обзор виртуализации сети Hyper-V](hyperv-network-virtualization-overview-windows-server.md)  
  
-   [Технический обзор виртуализации сети Hyper-V](hyperv-network-virtualization-technical-details-windows-server.md)  
  
-   [Программно-конфигурируемой сети](../../Software-Defined-Networking--SDN-.md)  
  