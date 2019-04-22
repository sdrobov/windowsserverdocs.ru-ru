---
title: Настройка программного балансировщика нагрузки для балансировки нагрузки и преобразования сетевых адресов (NAT)
description: Этот раздел является частью программно-Конфигурируемую сеть руководство о том, как управлять рабочими нагрузками клиента и виртуальными сетями в Windows Server 2016.
manager: dougkim
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 73bff8ba-939d-40d8-b1e5-3ba3ed5439c3
ms.author: pashort
author: shortpatti
ms.date: 08/23/2018
ms.openlocfilehash: 55847bfbc0362887497514009f6efe1312d79906
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59819355"
---
# <a name="configure-the-software-load-balancer-for-load-balancing-and-network-address-translation-nat"></a>Настройка программного балансировщика нагрузки для балансировки нагрузки и преобразования сетевых адресов (NAT)

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Можно использовать в этом разделе вы научитесь использовать программно-Конфигурируемую сеть \(SDN\) программной подсистемы балансировки нагрузки \(SLB\) для предоставления исходящих сетевых \(NAT\), NAT для входящего трафика и балансировка нагрузки между несколькими экземплярами приложения.

## <a name="software-load-balancer-overview"></a>Обзор подсистемы балансировки нагрузки программного обеспечения

Программная Подсистема балансировки нагрузки SDN \(SLB\) обеспечивает высокий уровень доступности и производительности сети для приложений. Это уровня 4 \(TCP, UDP\) который распределяет входящий трафик между работоспособными экземплярами службы в облачных службах или виртуальных машин, определенные в наборе подсистемы балансировки нагрузки балансировщик нагрузки.

Настройка SLB, выполнив следующие действия:

- Балансировка нагрузки входящего трафика внешним по отношению к виртуальной сети к виртуальным машинам \(виртуальных машин\), также называемый общедоступный виртуальный IP-адрес балансировки нагрузки.
- Балансировка нагрузки входящего трафика между виртуальными машинами в виртуальной сети, между виртуальными машинами в облачных службах или между локальными компьютерами и виртуальными машинами в виртуальной сети между локальными. 
- Перенаправлять сетевой трафик виртуальной Машины из виртуальной сети во внешние расположения, с помощью сетевых адресов (NAT), также называемый NAT для исходящего трафика
- Перенаправлять внешний трафик в определенную виртуальную машину, также называемый NAT для входящего трафика.




## <a name="example-create-a-public-vip-for-load-balancing-a-pool-of-two-vms-on-a-virtual-network"></a>Пример. Создание общедоступного виртуального IP-адреса для балансировки пул две виртуальные машины в виртуальной сети

В этом примере вы создадите объект подсистемы балансировки нагрузки с общедоступного виртуального IP-адреса и две виртуальные машины как члены пула для обслуживания запросов на VIP-адрес. Этот пример кода также добавляет проверки работоспособности HTTP для обнаружения ли один из членов пула становится недоступен.

1. Подготовьте объект подсистемы балансировки нагрузки.

   ```PowerShell
    import-module NetworkController

    $URI = "https://sdn.contoso.com"

    $LBResourceId = "LB2"

    $LoadBalancerProperties = new-object Microsoft.Windows.NetworkController.LoadBalancerProperties
   ```

2. Назначение внешнего IP-адреса, известен как виртуальный IP-адрес (VIP).<p>Виртуальный IP-адрес должен быть с неиспользуемый IP-адреса в одной логической сети пулов IP-адрес, присвоенный диспетчер подсистемы балансировки нагрузки. 

   ```PowerShell
    $VIPIP = "10.127.134.5"
    $VIPLogicalNetwork = get-networkcontrollerlogicalnetwork -ConnectionUri $uri -resourceid "PublicVIP" -PassInnerException
    
    $FrontEndIPConfig = new-object Microsoft.Windows.NetworkController.LoadBalancerFrontendIpConfiguration
    $FrontEndIPConfig.ResourceId = "FE1"
    $FrontEndIPConfig.ResourceRef = "/loadBalancers/$LBResourceId/frontendIPConfigurations/$($FrontEndIPConfig.ResourceId)"

    $FrontEndIPConfig.Properties = new-object Microsoft.Windows.NetworkController.LoadBalancerFrontendIpConfigurationProperties
    $FrontEndIPConfig.Properties.Subnet = new-object Microsoft.Windows.NetworkController.Subnet
    $FrontEndIPConfig.Properties.Subnet.ResourceRef = $VIPLogicalNetwork.Properties.Subnets[0].ResourceRef
    $FrontEndIPConfig.Properties.PrivateIPAddress = $VIPIP
    $FrontEndIPConfig.Properties.PrivateIPAllocationMethod = "Static"
      
    $LoadBalancerProperties.FrontEndIPConfigurations += $FrontEndIPConfig
   ```

3. Выделите пул внутренних адресов, который содержит динамические IP-адреса (DIP), входящих в состав элементов набора с балансировкой нагрузки виртуальных машин. 

   ```PowerShell 
    $BackEndAddressPool = new-object Microsoft.Windows.NetworkController.LoadBalancerBackendAddressPool
    $BackEndAddressPool.ResourceId = "BE1"
    $BackEndAddressPool.ResourceRef = "/loadBalancers/$LBResourceId/backendAddressPools/$($BackEndAddressPool.ResourceId)"

    $BackEndAddressPool.Properties = new-object Microsoft.Windows.NetworkController.LoadBalancerBackendAddressPoolProperties

    $LoadBalancerProperties.backendAddressPools += $BackEndAddressPool
   ```

4. Определите пробу работоспособности, для определения состояния работоспособности элементов внутреннего пула подсистемы балансировки нагрузки.<p>В этом примере проверку HTTP, который запрашивает вами для RequestPath из «/ health.htm.»  Запрос выполняется каждые 5 секунд, как указано в свойстве IntervalInSeconds.<p>При проверке работоспособности должен получить код ответа HTTP 200 для 11 последовательных запросов для проверки необходимо учитывать внутренних IP-адресов и работоспособным. Если IP-адрес серверной части не работоспособна, он не получает трафик от подсистемы балансировки нагрузки.

   >[!IMPORTANT]
   >Не блокируйте трафик из первого IP-адрес в подсети или для любого списков управления доступом (ACL), которые применяются к внутреннему IP-Адресу, потому что это точка происхождения для пробы.

   Используйте следующий пример для определения пробу работоспособности.

   ```PowerShell
    $Probe = new-object Microsoft.Windows.NetworkController.LoadBalancerProbe
    $Probe.ResourceId = "Probe1"
    $Probe.ResourceRef = "/loadBalancers/$LBResourceId/Probes/$($Probe.ResourceId)"

    $Probe.properties = new-object Microsoft.Windows.NetworkController.LoadBalancerProbeProperties
    $Probe.properties.Protocol = "HTTP"
    $Probe.properties.Port = "80"
    $Probe.properties.RequestPath = "/health.htm"
    $Probe.properties.IntervalInSeconds = 5
    $Probe.properties.NumberOfProbes = 11

    $LoadBalancerProperties.Probes += $Probe
   ```

5.  Определите правила для отправки трафик, поступающий на внешний IP-адрес в IP-адрес внутренней балансировки нагрузки.  В этом примере серверный пул принимает трафик TCP на порт 80.<p>Используйте следующий пример для определения правила балансировки нагрузки:

   ```PowerShell
    $Rule = new-object Microsoft.Windows.NetworkController.LoadBalancingRule
    $Rule.ResourceId = "webserver1"

    $Rule.Properties = new-object Microsoft.Windows.NetworkController.LoadBalancingRuleProperties
    $Rule.Properties.FrontEndIPConfigurations += $FrontEndIPConfig
    $Rule.Properties.backendaddresspool = $BackEndAddressPool 
    $Rule.Properties.protocol = "TCP"
    $Rule.Properties.FrontEndPort = 80
    $Rule.Properties.BackEndPort = 80
    $Rule.Properties.IdleTimeoutInMinutes = 4
    $Rule.Properties.Probe = $Probe

    $LoadBalancerProperties.loadbalancingRules += $Rule
   ```

6. Добавьте конфигурацию подсистемы балансировки нагрузки для сетевого контроллера.<p>Чтобы добавить конфигурацию подсистемы балансировки нагрузки для сетевого контроллера, используйте следующий пример:

   ```PowerShell
    $LoadBalancerResource = New-NetworkControllerLoadBalancer -ConnectionUri $URI -ResourceId $LBResourceId -Properties $LoadBalancerProperties -Force -PassInnerException
   ```

7. Выполните следующий пример, чтобы добавить эти сетевые интерфейсы в этот пул серверной части.


## <a name="example-use-slb-for-outbound-nat"></a>Пример. Использовать подсистему балансировки Нагрузки для NAT для исходящего Трафика

В этом примере настраивается SLB с помощью внутреннего пула для предоставления возможностей исходящего преобразования сетевых адресов для виртуальной Машины на пространство частных адресов виртуальной сети для доступа в Интернет. 

1. Создание свойства подсистемы балансировки нагрузки, внешний IP-адрес и серверный пул.

   ```PowerShell
    import-module NetworkController
    $URI = "https://sdn.contoso.com"

    $LBResourceId = "OutboundNATMMembers"
    $VIPIP = "10.127.134.6"

    $VIPLogicalNetwork = get-networkcontrollerlogicalnetwork -ConnectionUri $uri -resourceid "PublicVIP" -PassInnerException

    $LoadBalancerProperties = new-object Microsoft.Windows.NetworkController.LoadBalancerProperties

    $FrontEndIPConfig = new-object Microsoft.Windows.NetworkController.LoadBalancerFrontendIpConfiguration
    $FrontEndIPConfig.ResourceId = "FE1"
    $FrontEndIPConfig.ResourceRef = "/loadBalancers/$LBResourceId/frontendIPConfigurations/$($FrontEndIPConfig.ResourceId)"

    $FrontEndIPConfig.Properties = new-object Microsoft.Windows.NetworkController.LoadBalancerFrontendIpConfigurationProperties
    $FrontEndIPConfig.Properties.Subnet = new-object Microsoft.Windows.NetworkController.Subnet
    $FrontEndIPConfig.Properties.Subnet.ResourceRef = $VIPLogicalNetwork.Properties.Subnets[0].ResourceRef
    $FrontEndIPConfig.Properties.PrivateIPAddress = $VIPIP
    $FrontEndIPConfig.Properties.PrivateIPAllocationMethod = "Static"

    $LoadBalancerProperties.FrontEndIPConfigurations += $FrontEndIPConfig

    $BackEndAddressPool = new-object Microsoft.Windows.NetworkController.LoadBalancerBackendAddressPool
    $BackEndAddressPool.ResourceId = "BE1"
    $BackEndAddressPool.ResourceRef = "/loadBalancers/$LBResourceId/backendAddressPools/$($BackEndAddressPool.ResourceId)"
    $BackEndAddressPool.Properties = new-object Microsoft.Windows.NetworkController.LoadBalancerBackendAddressPoolProperties

    $LoadBalancerProperties.backendAddressPools += $BackEndAddressPool
   ```

2. Определите правила NAT для исходящего подключения.

   ```PowerShell
    $OutboundNAT = new-object Microsoft.Windows.NetworkController.LoadBalancerOutboundNatRule
    $OutboundNAT.ResourceId = "onat1"
    
    $OutboundNAT.properties = new-object Microsoft.Windows.NetworkController.LoadBalancerOutboundNatRuleProperties
    $OutboundNAT.properties.frontendipconfigurations += $FrontEndIPConfig
    $OutboundNAT.properties.backendaddresspool = $BackEndAddressPool
    $OutboundNAT.properties.protocol = "ALL"

    $LoadBalancerProperties.OutboundNatRules += $OutboundNAT
   ```

3. Добавьте объект подсистемы балансировки нагрузки на сетевом контроллере.

   ```PowerShell
    $LoadBalancerResource = New-NetworkControllerLoadBalancer -ConnectionUri $URI -ResourceId $LBResourceId -Properties $LoadBalancerProperties -Force -PassInnerException
   ```

4. Выполните следующий пример, чтобы добавить эти сетевые интерфейсы, к которым вы хотите предоставить доступ к Интернету.

## <a name="example-add-network-interfaces-to-the-back-end-pool"></a>Пример. Добавить сетевые интерфейсы в пуле серверной части
В этом примере добавить сетевые интерфейсы в пул серверной части.  Этот шаг необходимо повторить для каждого сетевого интерфейса, который может обрабатывать запросы к VIP-адрес. 

Можно также повторять этот процесс на один сетевой интерфейс, чтобы добавить его к нескольким объектам подсистемы балансировки нагрузки. Например, если у вас есть объект подсистемы балансировки нагрузки для VIP-адрес web server и объект балансировщика нагрузки на отдельные для предоставления NAT для исходящего трафика
    
1. Получите объект подсистемы балансировки нагрузки, содержащий серверный пул, чтобы добавить сетевой интерфейс.

   ```PowerShell
   $lbresourceid = "LB2"
   $lb = get-networkcontrollerloadbalancer -connectionuri $uri -resourceID $LBResourceId -PassInnerException
  ```

2. Получить сетевой интерфейс и добавить в пул backendaddress loadbalancerbackendaddresspools массив.

   ```PowerShell
   $nic = get-networkcontrollernetworkinterface  -connectionuri $uri -resourceid 6daca142-7d94-0000-1111-c38c0141be06 -PassInnerException
   $nic.properties.IpConfigurations[0].properties.LoadBalancerBackendAddressPools += $lb.properties.backendaddresspools[0]
   ```  

3. Поместите сетевой интерфейс, чтобы применить изменение. 

   ```PowerShell
   new-networkcontrollernetworkinterface  -connectionuri $uri -resourceid 6daca142-7d94-0000-1111-c38c0141be06 -properties $nic.properties -force -PassInnerException
   ``` 


## <a name="example-use-the-software-load-balancer-for-forwarding-traffic"></a>Пример. Использовать подсистему балансировки нагрузки программного обеспечения для пересылки трафика
Если вам нужно сопоставить виртуальный IP-адрес к одному сетевому интерфейсу в виртуальной сети без определения отдельных портов, можно создать правило переадресации L3.  Это правило перенаправляет весь трафик из виртуальной Машины с помощью назначенного виртуального IP-адреса, содержащимися в объекте PublicIPAddress.

Если вы определили VIP и DIP как одной и той же подсети, затем это эквивалентно выполнению переадресации L3 без NAT.

>[!NOTE]
>Этот процесс не требуется для создания объекта подсистемы балансировки нагрузки.  Назначение ресурса PublicIPAddress с сетевым интерфейсом является достаточно информации для подсистемы балансировки нагрузки программного обеспечения выполнить его настройку.


1. Создается объект общедоступного IP-адрес должен содержать виртуальный IP-адрес.

   ```PowerShell
   $publicIPProperties = new-object Microsoft.Windows.NetworkController.PublicIpAddressProperties
   $publicIPProperties.ipaddress = "10.127.134.7"
   $publicIPProperties.PublicIPAllocationMethod = "static"
   $publicIPProperties.IdleTimeoutInMinutes = 4
   $publicIP = New-NetworkControllerPublicIpAddress -ResourceId "MyPIP" -Properties $publicIPProperties -ConnectionUri $uri -Force -PassInnerException
   ```

2. Назначение ресурса PublicIPAddress с сетевым интерфейсом.

   ```PowerShell
   $nic = get-networkcontrollernetworkinterface  -connectionuri $uri -resourceid 6daca142-7d94-0000-1111-c38c0141be06
   $nic.properties.IpConfigurations[0].Properties.PublicIPAddress = $publicIP
   New-NetworkControllerNetworkInterface -ConnectionUri $uri -ResourceId $nic.ResourceId -Properties $nic.properties -PassInnerException
   ```

## <a name="example-use-the-software-load-balancer-for-forwarding-traffic-with-a-dynamically-allocated-vip"></a>Пример. Использовать подсистему балансировки нагрузки программного обеспечения для пересылки трафика с динамически выделяемый виртуальных IP-адресов
В этом примере повторяется то же действие, что и предыдущий, но он автоматически выделяет VIP-адрес из доступного пула виртуальных IP-адресов в подсистеме балансировки нагрузки вместо указания конкретного IP-адреса. 

1. Создается объект общедоступного IP-адрес должен содержать виртуальный IP-адрес.

   ```PowerShell
   $publicIPProperties = new-object Microsoft.Windows.NetworkController.PublicIpAddressProperties
   $publicIPProperties.PublicIPAllocationMethod = "dynamic"
   $publicIPProperties.IdleTimeoutInMinutes = 4
   $publicIP = New-NetworkControllerPublicIpAddress -ResourceId "MyPIP" -Properties $publicIPProperties -ConnectionUri $uri -Force -PassInnerException
   ```

2. Запрос ресурса PublicIPAddress, чтобы определить, какие IP-адрес был назначен.

   ```PowerShell
    (Get-NetworkControllerPublicIpAddress -ConnectionUri $uri -ResourceId "MyPIP").properties
   ```

   Свойство IP-адрес содержит адрес, назначенный.  Выходные данные будут выглядеть примерно следующим образом:
   ```
    Counters                 : {}
    ConfigurationState       :
    IpAddress                : 10.127.134.2
    PublicIPAddressVersion   : IPv4
    PublicIPAllocationMethod : Dynamic
    IdleTimeoutInMinutes     : 4
    DnsSettings              :
    ProvisioningState        : Succeeded
    IpConfiguration          :
    PreviousIpConfiguration  :
   ```
 
1. Назначение ресурса PublicIPAddress с сетевым интерфейсом.

   ```PowerShell
   $nic = get-networkcontrollernetworkinterface  -connectionuri $uri -resourceid 6daca142-7d94-0000-1111-c38c0141be06
   $nic.properties.IpConfigurations[0].Properties.PublicIPAddress = $publicIP
   New-NetworkControllerNetworkInterface -ConnectionUri $uri -ResourceId $nic.ResourceId -Properties $nic.properties -PassInnerException
   ```
## <a name="example-remove-a-publicip-address-that-is-being-used-for-forwarding-traffic-and-return-it-to-the-vip-pool"></a>Пример. Удалить адрес общедоступный IP-адрес, который используется для пересылки трафика и вернуть его в пул виртуальных IP-адресов
В этом примере удаляется ресурс PublicIPAddress созданного в предыдущих примерах.  После удаления ресурса PublicIPAddress ссылка PublicIPAddress будет автоматически удалена из сетевого интерфейса, трафик будет остановлено пересылку и IP-адрес будет возвращаться в пул общедоступных виртуальных IP-адресов для повторного использования.  

1. Удалить общедоступный IP-адрес

   ```PowerShell
   Remove-NetworkControllerPublicIPAddress -ConnectionURI $uri -ResourceId "MyPIP"
   ```

---


 