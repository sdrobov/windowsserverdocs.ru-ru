---
title: Использование виртуальных сетевых устройств в виртуальной сети
description: Этот раздел является частью программного обеспечения определены сетевые руководство о том, как управление рабочими нагрузками клиента и виртуальные сети в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: networking-sdn
ms.assetid: 3c361575-1050-46f4-ac94-fa42102f83c1
ms.author: pashort
author: shortpatti
ms.openlocfilehash: db46189931263d230f013431f319eb2497589dee
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="use-network-virtual-appliances-on-a-virtual-network"></a>Использование виртуальных сетевых устройств в виртуальной сети

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать, чтобы узнать, как развертывание виртуальных сетевых устройств в клиенте виртуальных сетей.

Виртуальных сетевых устройств можно добавить к сетям, которые выполняют определенные пользователем маршрутизации и функции зеркалирования портов.

Этот раздел содержит следующие разделы.

- [Типы виртуальных сетевых устройств](#bkmk_types)
- [Развертывание виртуального устройства сети](#bkmk_deploy)
- [Пример:: Маршрутизации пользователем.](#bkmk_routing)
- [Пример: Зеркалирование портов](#bkmk_port)

## <a name="bkmk_types"></a>Типы виртуальных сетевых устройств

Существует два типа виртуальных устройств, которые можно использовать в виртуальных сетях.

1. **Задано пользователем маршрутизации**. Определенные пользователем маршрутизации заменяет распределенных маршрутизаторы в виртуальной сети маршрутизации возможности виртуального устройства.  С пользователем маршрутизации виртуальное устройство используется в качестве маршрутизатора между виртуальными подсетями виртуальной сети.
2. **Зеркалирование портов**. Зеркалирования портов, весь сетевой трафик, вход и выход из отслеживаемых порт копируется и отправляется виртуальное устройство для анализа. 
## <a name="bkmk_deploy"></a>Развертывание виртуального устройства сети

Для развертывания виртуального устройства, необходимо сначала создать виртуальную машину (VM), содержащий устройства и затем подключить ВМ виртуальных подсетей.

>[!NOTE]
>Дополнительные сведения см. в разделе [создания виртуальной Машины клиента и подключение к виртуальной сети клиента или виртуальной локальной сети](Create-a-Tenant-VM.md)

Некоторые устройства требуется несколько виртуальных сетевых адаптеров. Обычно один сетевой адаптер, предназначенный для управления устройством, хотя дополнительные адаптеры используются для обработки трафика. 

Если для вашего устройства требуется несколько сетевых адаптеров, необходимо создать каждого сетевого интерфейса в сетевого контроллера. 

Также необходимо назначить идентификатор интерфейса на каждом узле для каждого из дополнительных адаптеры, которые находятся на разных виртуальных подсетей.

После завершения развертывания сети виртуальное устройство устройства можно использовать для маршрутизации определенные пользователем, зеркалирование портов или оба.

##<a name="bkmk_routing"></a>Пример:: Маршрутизации пользователем.

Для большинства сред необходимо будет только маршруты системы, уже определены распределенного маршрутизатора виртуальной сети. Тем не менее может потребоваться создать таблицу маршрутизации и добавьте один или несколько маршрутов, в определенных случаях, например:

* Принудительное туннелирование к Интернету через локальную сеть.
* Использование виртуальных устройств в вашей среде.

В этих сценариях необходимо создать таблицу маршрутизации и добавлять пользовательские маршруты в таблицу. У вас есть несколько таблиц маршрута и той же таблицы маршрутизации могут быть связаны с одной или несколькими подсетями. 

Каждая подсеть может быть связан только с таблицей один маршрут. Все виртуальные машины в подсети, используйте таблицу маршрутизации, который связан с этой подсети.

Подсети используют маршруты системы пока таблицу маршрутизации связан подсети. После существует связь, маршрутизации осуществляется на основе на максимальную длину префикса соответствия (LPM) между пользователем маршруты и маршруты системы. 

Если существует несколько маршрутов с помощью того же соответствием LPM, определенному маршруту пользователя выбирается сначала - перед маршрута системы. 

###<a name="step-1-create-the-route-table-properties"></a>Шаг 1: Создание маршрута свойства таблицы

В этой таблице маршрута будет содержать все определенные пользователем маршрутов.  Маршруты системы по-прежнему применяются в соответствии с правилами, описанный выше.

В следующем примере показан можно использовать для создания свойства таблицы маршрутизации.

    $routetableproperties = new-object Microsoft.Windows.NetworkController.RouteTableProperties

###<a name="step-2-add-a-route-to-the-route-table-properties"></a>Шаг 2: Добавление маршрута для свойства таблицы маршрутизации

Этот маршрут говорит, отправляемых любой трафик, который предназначен для подсети 12.0.0.0/8 виртуальное устройство в 192.168.1.10 маршрутизации.  Очень важно, что устройство имеет виртуального сетевого адаптера, подключенных к виртуальной сети, IP-адрес, назначенный сетевому интерфейсу.

Добавление маршрута для свойства таблицы маршрута можно использовать команды в следующем примере.

    $route = new-object Microsoft.Windows.NetworkController.Route
    $route.ResourceID = "0_0_0_0_0"
    $route.properties = new-object Microsoft.Windows.NetworkController.RouteProperties
    $route.properties.AddressPrefix = "0.0.0.0/0"
    $route.properties.nextHopType = "VirtualAppliance"
    $route.properties.nextHopIpAddress = "192.168.1.10"
    $routetableproperties.routes += $route

Повторите этот шаг для каждого маршрута, которые требуется определить, можно добавить дополнительные маршруты.
s
###<a name="step-3-add-the-route-table-to-network-controller"></a>Шаг 3: Добавление в таблицу маршрутизации для сетевого контроллера
Чтобы добавить в таблицу маршрутизации для сетевого контроллера можно использовать команды в следующем примере.

    $routetable = New-NetworkControllerRouteTable -ConnectionUri $uri -ResourceId "Route1" -Properties $routetableproperties

###<a name="step-4-apply-the-route-table-to-the-virtual-subnet"></a>Шаг 4: Применение в таблицу маршрутизации виртуальной подсети
 
При применении в таблицу маршрутизации виртуальной подсети, первый виртуальной подсети в сети Tenant1_Vnet1 использует таблицу маршрутизации. Можно назначить в таблицу маршрутизации столько подсетей в виртуальной сети как требуется.

В следующем примере показан можно использовать для применения к виртуальную подсеть в таблицу маршрутизации.

    $vnet = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "Tenant1_VNet1"
    $vnet.properties.subnets[0].properties.RouteTable = $routetable
    new-networkcontrollervirtualnetwork -connectionuri $uri -properties $vnet.properties -resourceId $vnet.resourceid

Как только в таблицу маршрутизации применить к виртуальной сети, перенаправляется трафик виртуального устройства. Необходимо настроить таблицу маршрутизации в виртуальное устройство для пересылки трафика, таким образом, подходящие для используемой среды.

##<a name="bkmk_port"></a>Пример: Зеркалирование портов

В этом примере позволяет настроить трафика MyVM_Ethernet1 таким образом, чтобы трафик зеркалируется Appliance_Ethernet1.

В этом примере предполагается, что уже развернули две виртуальные машины, как устройства и виртуальной машины для отслеживания с зеркальным отображением.

Очень важно, что устройства имеет второй сетевой адаптер для управления, так как после зеркалирования включена в качестве назначения на Appliance_Ethernet1, он больше не будет получать трафика, предназначенного для IP-интерфейса, настроен.

###<a name="step-1-get-the-virtual-network-on-which-your-vms-are-located"></a>Шаг 1: Получите виртуальной сети, на котором расположены ВМ
Следующий пример команды можно использовать для получения виртуальной сети.

    $vnet = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "Tenant1_VNet1"

###<a name="step-2-get-the-network-controller-network-interfaces-for-the-mirroring-source-and-destination"></a>Шаг 2: Получение сетевого контроллера сетевых интерфейсов для зеркального отображения источника и назначения
Для получения сетевого контроллера сетевых интерфейсов для зеркального отображения источника и назначения можно использовать команды в следующем примере.

    $dstNic = get-networkcontrollernetworkinterface -ConnectionUri $uri -ResourceId "Appliance_Ethernet1"
    $srcNic = get-networkcontrollernetworkinterface -ConnectionUri $uri -ResourceId "MyVM_Ethernet1"

###<a name="step-3-create-a-serviceinsertionproperties-object-to-contain-the-port-mirroring-rules-and-the-element-which-represents-the-destination-interface"></a>Шаг 3: Создание объект serviceinsertionproperties может содержать зеркалирование правила и элемент, который представляет интерфейс конечного порта
В следующем примере показан можно использовать для создания объекта serviceinsertionproperties назначения.

    $portmirror = [Microsoft.Windows.NetworkController.ServiceInsertionProperties]::new()
    $portMirror.Priority = 1

###<a name="step-4-create-a-serviceinsertionrules-object-to-contain-the-rules-that-must-be-matched-in-order-for-the-traffic-to-be-sent-to-the-appliance"></a>Шаг 4: Создание объект serviceinsertionrules может содержать правила, которые совпадающих для передачи трафика, отправляемого устройства

Правила, определенный ниже, соответствие весь трафик, входящий и исходящий, представляющий традиционных зеркала.  Эти правила можно настроить, если вы заинтересованы в зеркальном отображении конкретный порт или определенного источника и назначения.

В следующем примере показан можно использовать для создания объекта serviceinsertionproperties.

    $portmirror.ServiceInsertionRules = [Microsoft.Windows.NetworkController.ServiceInsertionRule[]]::new(1)

    $portmirror.ServiceInsertionRules[0] = [Microsoft.Windows.NetworkController.ServiceInsertionRule]::new()
    $portmirror.ServiceInsertionRules[0].ResourceId = "Rule1"
    $portmirror.ServiceInsertionRules[0].Properties = [Microsoft.Windows.NetworkController.ServiceInsertionRuleProperties]::new()

    $portmirror.ServiceInsertionRules[0].Properties.Description = "Port Mirror Rule"
    $portmirror.ServiceInsertionRules[0].Properties.Protocol = "All"
    $portmirror.ServiceInsertionRules[0].Properties.SourcePortRangeStart = "0"
    $portmirror.ServiceInsertionRules[0].Properties.SourcePortRangeEnd = "65535"
    $portmirror.ServiceInsertionRules[0].Properties.DestinationPortRangeStart = "0"
    $portmirror.ServiceInsertionRules[0].Properties.DestinationPortRangeEnd = "65535"
    $portmirror.ServiceInsertionRules[0].Properties.SourceSubnets = "*"
    $portmirror.ServiceInsertionRules[0].Properties.DestinationSubnets = "*"

###<a name="step-5-create-a-serviceinsertionelements-object-to-contain-the-network-interface-of-the-appliance-you-are-mirroring-to"></a>Шаг 5: Создание serviceinsertionelements объекта, который содержит сетевой интерфейс устройства, которую вы зеркального отображения
В следующем примере показан можно использовать для создания объекта serviceinsertionelements сетевого интерфейса.

    $portmirror.ServiceInsertionElements = [Microsoft.Windows.NetworkController.ServiceInsertionElement[]]::new(1)

    $portmirror.ServiceInsertionElements[0] = [Microsoft.Windows.NetworkController.ServiceInsertionElement]::new()
    $portmirror.ServiceInsertionElements[0].ResourceId = "Element1"
    $portmirror.ServiceInsertionElements[0].Properties = [Microsoft.Windows.NetworkController.ServiceInsertionElementProperties]::new()

    $portmirror.ServiceInsertionElements[0].Properties.Description = "Port Mirror Element"
    $portmirror.ServiceInsertionElements[0].Properties.NetworkInterface = $dstNic
    $portmirror.ServiceInsertionElements[0].Properties.Order = 1

###<a name="step-6-add-the-service-insertion-object-in-network-controller"></a>Шаг 6: Добавление вставки объект службы в сетевого контроллера
При выполнении команды, приведет к остановке всего трафика к сетевому интерфейсу устройства, указанного на предыдущем шаге.

Добавление объекта вставки службы в сетевого контроллера можно использовать команды в следующем примере.

    $portMirror = New-NetworkControllerServiceInsertion -ConnectionUri $uri -Properties $portmirror -ResourceId "MirrorAll"

###<a name="step-7-update-the-network-interface-of-the-source-to-be-mirrored"></a>Шаг 7: Обновите сетевой интерфейс источника зеркальное отражение
Чтобы обновить сетевой интерфейс, можно использовать команды в следующем примере.

    $srcNic.Properties.IpConfigurations[0].Properties.ServiceInsertion = $portMirror
    $srcNic = New-NetworkControllerNetworkInterface -ConnectionUri $uri  -Properties $srcNic.Properties -ResourceId $srcNic.ResourceId

После завершения этих шагов зеркальное отображение трафик от интерфейса MyVM_Ethernet1 осуществляется с помощью интерфейса Appliance_Ethernet1.
 
