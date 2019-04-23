---
title: Использование виртуальных сетевых устройств в виртуальной сети
description: В этом разделе вы узнаете, как развертывание виртуальных сетевых модулей в виртуальных сетях клиента. Виртуальные сетевые модули можно добавить к сетям, которые выполняют определяемых пользователем маршрутах и зеркального отображения функций портов.
manager: dougkim
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
ms.date: 08/30/2018
ms.openlocfilehash: e715a782651a5b9867f3b45251fd6ea6e4a9e4f7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59847375"
---
# <a name="use-network-virtual-appliances-on-a-virtual-network"></a>Использование виртуальных сетевых устройств в виртуальной сети

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе вы узнаете, как развертывание виртуальных сетевых модулей в виртуальных сетях клиента. Виртуальные сетевые модули можно добавить к сетям, которые выполняют определяемых пользователем маршрутах и зеркального отображения функций портов.

## <a name="types-of-network-virtual-appliances"></a>Типы сетевых виртуальных устройств

Можно использовать один из двух типов виртуальных устройств:

1. **Определяемая пользователем маршрутизация** -заменяет распределенных маршрутизаторы в виртуальной сети возможности маршрутизации виртуального устройства.  С помощью определяемых пользователем маршрутах, виртуальное устройство используется как маршрутизатор между виртуальными подсетями в виртуальной сети.

2. **Зеркальное отображение портов** — весь сетевой трафик, который вводит или выходя из отслеживаемых портов копируется и отправляется виртуальный модуль для анализа. 


## <a name="deploying-a-network-virtual-appliance"></a>Развертывание виртуального сетевого устройства

Чтобы развернуть виртуальный сетевой модуль, необходимо сначала создать виртуальную Машину, которая содержит устройства и подключитесь к соответствующей виртуальной сети подсети виртуальной Машины. Дополнительные сведения см. в разделе [Создание виртуальной Машины клиента и подключение к виртуальной сети клиента или виртуальной локальной сети](Create-a-Tenant-VM.md).

Некоторые устройства требуется несколько виртуальных сетевых адаптеров. Как правило, один сетевой адаптер, предназначенный для управления устройством, хотя дополнительные адаптеры обработки трафика.  Если для вашего устройства требуется несколько сетевых адаптеров, необходимо создать каждого сетевого интерфейса на сетевом контроллере. Также необходимо назначить идентификатор интерфейса на каждом узле для каждого из дополнительных адаптеров, которые находятся в разных виртуальных подсетей.

После развертывания сетевого виртуального модуля, можно использовать устройства, для определенных маршрутизации, переносу зеркального отображения или оба. 


## <a name="example-user-defined-routing"></a>Пример. Определяемые пользователем маршруты

Для большинства сред достаточно только системных маршрутов, уже определен распределенного маршрутизатора виртуальной сети. Тем не менее может потребоваться создать таблицу маршрутизации и добавьте один или несколько маршрутов в определенных случаях, например:

- Принудительное туннелирование в Интернет с помощью вашей локальной сети.
- Использование виртуальных устройств в вашей среде.

В таких случаях необходимо создать таблицу маршрутизации и добавить определяемые пользователем маршруты в таблицу. Можно использовать несколько таблиц маршрутизации, а вы можете сопоставить той же таблицы маршрутизации для одной или несколькими подсетями. Можно связать только каждой подсети с одной таблицей маршрутизации. Все виртуальные машины в подсети используют таблицу маршрутизации, связана с подсетью.

Системные маршруты пока использует таблицу маршрутизации связывается с подсетью. После связь установлена, маршрутизация выполняется на основе на длинного префикса (LPM) среди определяемых пользователем маршрутов и системных маршрутов. Если имеется несколько маршрутов с одинаковыми совпадениями LPM, определяемый пользователем маршрут выбирается first - прежде чем системный маршрут.
 
**Процедура.**

1. Создайте маршрут свойства таблицы, которое содержит все определяемые пользователем маршруты.<p>Системные маршруты по-прежнему применяются в соответствии с определенными выше правилами.

   ```PowerShell
    $routetableproperties = new-object Microsoft.Windows.NetworkController.RouteTableProperties
   ```

2. Добавьте маршрут свойства таблицы маршрутизации.<p>Ни одному маршруту, предназначенный для подсети 12.0.0.0/8 будет перенаправляться на виртуальное устройство в 192.168.1.10. Модуль должен иметь виртуального сетевого адаптера, подключенных к виртуальной сети с этого IP-адрес назначается сетевой интерфейс.

   ```PowerShell
    $route = new-object Microsoft.Windows.NetworkController.Route
    $route.ResourceID = "0_0_0_0_0"
    $route.properties = new-object Microsoft.Windows.NetworkController.RouteProperties
    $route.properties.AddressPrefix = "0.0.0.0/0"
    $route.properties.nextHopType = "VirtualAppliance"
    $route.properties.nextHopIpAddress = "192.168.1.10"
    $routetableproperties.routes += $route
   ```
   >[!TIP]
   >Если вы хотите добавить дополнительные маршруты, повторите этот шаг для каждого маршрута, который вы хотите определить.

3. Добавьте таблицу маршрутизации для сетевого контроллера.

   ```PowerShell
    $routetable = New-NetworkControllerRouteTable -ConnectionUri $uri -ResourceId "Route1" -Properties $routetableproperties
   ```

4. Применение таблицы маршрутизации к виртуальной подсети.<p>Применение таблицы маршрутов к виртуальной подсети, первой виртуальной подсети в сети Tenant1_Vnet1 использует таблицу маршрутов. Можно назначить таблице столько подсетей в виртуальной сети необходимо.

   ```PowerShell
    $vnet = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "Tenant1_VNet1"
    $vnet.properties.subnets[0].properties.RouteTable = $routetable
    new-networkcontrollervirtualnetwork -connectionuri $uri -properties $vnet.properties -resourceId $vnet.resourceid
   ```

Сразу же применить таблицу маршрутизации в виртуальную сеть, трафик передается в виртуальное устройство. Необходимо настроить таблицы маршрутизации в виртуальный модуль для пересылки трафика, таким образом, подходящие для используемой среды.

## <a name="example-port-mirroring"></a>Пример. Зеркальное отображение портов

В этом примере следует настроить трафик MyVM_Ethernet1 Appliance_Ethernet1 зеркальный сервер.  Мы предполагаем, что вы развернули две виртуальные машины, как устройства, а другой — как виртуальную Машину для мониторинга с зеркальным отображением. 

Модуль должен иметь второй сетевой интерфейс для управления. После включения зеркального отображения в качестве места назначения на Appliciance_Ethernet1, больше не получает трафик, предназначенный для IP-интерфейса настроена существует.


**Процедура.**

1. Получите виртуальную сеть, на котором размещены виртуальные машины.

   ```PowerShell
   $vnet = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "Tenant1_VNet1"
   ```

2. Получение сетевых интерфейсов сетевого контроллера для зеркального отображения источника и назначения.

   ```PowerShell
   $dstNic = get-networkcontrollernetworkinterface -ConnectionUri $uri -ResourceId "Appliance_Ethernet1"
   $srcNic = get-networkcontrollernetworkinterface -ConnectionUri $uri -ResourceId "MyVM_Ethernet1"
   ```

3. Создайте объект serviceinsertionproperties должен содержать зеркального отображения правил и элемент, который представляет интерфейс назначения портов.

   ```PowerShell
   $portmirror = [Microsoft.Windows.NetworkController.ServiceInsertionProperties]::new()
   $portMirror.Priority = 1
   ```

4. Создайте объект serviceinsertionrules должен содержать правила, которые должны совпадать для передачи трафика, отправляемого к устройству.<p>Определить правила ниже совпадение весь трафик, входящий и исходящий, представляющий традиционных зеркала.  Вы можете настроить эти правила, если вы заинтересованы в зеркальном отображении, конкретного порта или определенного источника и назначения.

   ```PowerShell
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
   ```

5. Создайте объект serviceinsertionelements должен содержать сетевой интерфейс зеркального устройства.

   ```PowerShell
   $portmirror.ServiceInsertionElements = [Microsoft.Windows.NetworkController.ServiceInsertionElement[]]::new(1)

   $portmirror.ServiceInsertionElements[0] = [Microsoft.Windows.NetworkController.ServiceInsertionElement]::new()
   $portmirror.ServiceInsertionElements[0].ResourceId = "Element1"
   $portmirror.ServiceInsertionElements[0].Properties = [Microsoft.Windows.NetworkController.ServiceInsertionElementProperties]::new()

   $portmirror.ServiceInsertionElements[0].Properties.Description = "Port Mirror Element"
   $portmirror.ServiceInsertionElements[0].Properties.NetworkInterface = $dstNic
   $portmirror.ServiceInsertionElements[0].Properties.Order = 1
   ```

6. Добавление в службу вставки объекта в сетевой контроллер.<p>При выполнении команды, весь трафик к устройству сетевой интерфейс, указанный в предыдущем шаге останавливается.

   ```PowerShell
   $portMirror = New-NetworkControllerServiceInsertion -ConnectionUri $uri -Properties $portmirror -ResourceId "MirrorAll"
   ```

7. Обновление сетевого интерфейса источника для зеркального отображения.

   ```PowerShell
   $srcNic.Properties.IpConfigurations[0].Properties.ServiceInsertion = $portMirror
   $srcNic = New-NetworkControllerNetworkInterface -ConnectionUri $uri  -Properties $srcNic.Properties -ResourceId $srcNic.ResourceId
   ```

После выполнения этих действий, интерфейс Appliance_Ethernet1 отражает трафик от интерфейса MyVM_Ethernet1.
 
---