---
title: Настройка программного балансировщика нагрузки для балансировки нагрузки и преобразования сетевых адресов (NAT)
description: Этот раздел является частью программного обеспечения определены сетевые руководство о том, как управление рабочими нагрузками клиента и виртуальные сети в Windows Server 2016.
manager: brianlic
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
ms.openlocfilehash: 7f0393db564061caa0bc8f18b1d623f24749b46c
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="configure-the-software-load-balancer-for-load-balancing-and-network-address-translation-nat"></a>Настройка программного балансировщика нагрузки для балансировки нагрузки и преобразования сетевых адресов (NAT)

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать чтобы узнать, как использовать определенные сетевые программного обеспечения \(SDN\) программного балансировщика нагрузки \(SLB\) для исходящих сетевых адресов NAT, входящего трафика NAT или Балансировка нагрузки между несколькими экземплярами приложения.

Этот раздел содержит следующие разделы.

- [Обзор подсистемы балансировки нагрузки программного обеспечения](#bkmk_slbover)
- [Пример: Создание общих виртуальных IP-адресов для пула двух виртуальных машин в виртуальной сети балансировки нагрузки](#bkmk_publicvip)
- [Пример: Использование SLB для исходящего NAT](#bkmk_obnat)
- [Пример: Добавление сетевых интерфейсов в пул серверной части](#bkmk_backend)
- [Пример: Использование подсистемы балансировки нагрузки программного обеспечения для пересылки трафика](#bkmk_forward)

## <a name="bkmk_slbover"></a>Обзор подсистемы балансировки нагрузки программного обеспечения

Балансировка нагрузки программного обеспечения SDN \(SLB\) доставляет высокой производительности, доступности и сетевой приложений. Это 4 уровня \ балансировщика, которая распределяет трафик между экземплярами работоспособность в облачных служб или виртуальных машин, определенных в наборе подсистемы балансировки нагрузки нагрузки (TCP, UDP\).

Вы можете настроить SLB делать следующее.

* Нагрузки баланс входящий трафик внешних по отношению к виртуальной сети для виртуальных машин \(VMs\). Это называется балансировки нагрузки общедоступных виртуальных IP-адресов.
* Нагрузки баланс входящий трафик между виртуальными машинами в виртуальной сети, а также между виртуальными машинами в облачных службах или между локальными компьютерами и виртуальных машин в виртуальной сети перекрестные. 
* Перенаправление трафика сети виртуальной Машины из виртуальной сети на внешние источники, с помощью преобразование сетевых адресов (NAT).  Это называется исходящих NAT.
* Пересылка внешнего трафика определенной виртуальной Машине.  Это называется входящий NAT.

>[!IMPORTANT]
>Это известная проблема запрещает объекты подсистемы балансировки нагрузки в модуле NetworkController Windows PowerShell правильно работает в Windows Server 2016 5. Чтобы обойти эту проблему — использовать динамического хэш-таблицы и Invoke-WebRequest вместо. Этот метод показано в следующих примерах.


## <a name="bkmk_publicvip"></a>Пример: Создание общих виртуальных IP-адресов для пула двух виртуальных машин в виртуальной сети балансировки нагрузки

Этот пример можно использовать для создания объекта подсистемы балансировки нагрузки с общедоступных виртуальных IP-адресов и две виртуальные машины как члены группы для обслуживания запросов к VIP.  В этом примере кода также добавляет проверку работоспособности HTTP, для обнаружения, является ли один из членов группы недоступность.

###<a name="step-1-prepare-the-load-balancer-object"></a>Шаг 1: Подготовка объект подсистемы балансировки нагрузки
Следующий пример можно использовать для подготовки объект подсистемы балансировки нагрузки.

    $lbresourceId = "LB2"

    $lbproperties = @{}
    $lbproperties.frontendipconfigurations = @()
    $lbproperties.backendAddressPools = @()
    $lbproperties.probes = @()
    $lbproperties.loadbalancingRules = @()
    $lbproperties.OutboundNatRules = @()

###<a name="step-2-assign-a-front-end-ip"></a>Шаг 2: Назначьте IP-интерфейса
Интерфейсный IP часто называют как виртуальные IP-адресов (VIP).  VIP должна быть получена с неиспользуемые IP-адреса в одной логической сети пула IP-адресов, который ранее присвоенный диспетчер балансировки нагрузки.

Следующий пример можно использовать для назначения внешнего IP-адреса.

    $vipip = "10.127.132.5"
    $vipln = get-networkcontrollerlogicalnetwork -ConnectionUri $uri -resourceid "f8f67956-3906-4303-94c5-09cf91e7e311"

    $fe = @{}
    $fe.resourceId = "FE1"
    $fe.resourceRef = "/loadBalancers/$lbresourceId/frontendIPConfigurations/$($fe.resourceId)"
    $fe.properties = @{}
    $fe.properties.subnet = @{}
    $fe.properties.subnet.ResourceRef = $vipln.properties.Subnets[0].ResourceRef
    $fe.properties.privateIPAddress = $vipip
    $fe.properties.privateIPAllocationMethod = "Static"
    $lbproperties.frontendipconfigurations += $fe

###<a name="step-3-allocate-a-backend-address-pool"></a>Шаг 3: Выделение пула адресов серверная часть
Пул адресов внутренних содержит динамических IP-адресов (DIP), составляющих элементы набора балансировкой нагрузки виртуальных машин. На этом шаге только выделить пул. IP-конфигурации, добавляются в более позднем этапе.

Следующий пример можно использовать для распределения пула адресов серверной части.
 
    $backend = @{}
    $backend.resourceId = "BE1"
    $backend.resourceRef = "/loadBalancers/$lbresourceId/backendAddressPools/$($backend.resourceId)"
    $lbproperties.backendAddressPools += $backend

###<a name="step-4-define-a-health-probe"></a>Шаг 4: Определение проверки работоспособности
Проверки работоспособности для определения состояния работоспособности членов пула внутренних используются подсистемы балансировки нагрузки. В этом примере определить проверку HTTP, который запрашивает для RequestPath из» и health.htm».  Запрос выполняется каждые 5 секунд, как указано в свойстве IntervalInSeconds.

Проверка индекса должен получить код ответа HTTP 200 11 последовательных запросов для проверки внутренних IP-адрес, работоспособность. Если внутренний IP-адресов находится в неработоспособном состоянии, подсистема балансировки нагрузки не будет отправлять трафик IP.

>[!Note]
>Очень важно, что любой списки управления доступом, применяемых для внутренних IP-адреса не блокируют трафик первый IP-адресов в подсети, так как источник отправки для проверки.

Следующий пример можно использовать для определения проверки работоспособности.
 
    $lbprobe = @{}
    $lbprobe.ResourceId = "Probe1"
    $lbprobe.resourceRef = "/loadBalancers/$lbresourceId/Probes/$($lbprobe.resourceId)"
    $lbprobe.properties = @{}
    $lbprobe.properties.protocol = "HTTP"
    $lbprobe.properties.port = "80"
    $lbprobe.properties.RequestPath = "/health.htm"
    $lbprobe.properties.IntervalInSeconds = 5
    $lbprobe.properties.NumberOfProbes = 11
    $lbproperties.probes += $lbprobe

###<a name="step-5-define-a-load-balancing-rule"></a>Шаг 5: Определение правила балансировки нагрузки
Это правило балансировки нагрузки определяет, как трафик, поступающий на интерфейсном IP-адресов, не должны отправляться на внутренний IP-адресов.  В этом примере TCP-трафика на порт 80 отправляется в пул серверной части.

Следующий пример можно использовать для определения правила балансировки нагрузки.

    $lbrule = @{}
    $lbrule.ResourceId = "webserver1"
    $lbrule.properties = @{}
    $lbrule.properties.FrontEndIPConfigurations = @()
    $lbrule.properties.FrontEndIPConfigurations += $fe
    $lbrule.properties.backendaddresspool = $backend 
    $lbrule.properties.protocol = "TCP"
    $lbrule.properties.frontendPort = 80
    $lbrule.properties.Probe = $lbprobe
    $lbproperties.loadbalancingRules += $lbrule

###<a name="step-6-add-the-load-balancer-configuration-to-network-controller"></a>Шаг 6: Добавление настройке подсистемы балансировки нагрузки для сетевого контроллера
До сих в этом примере все созданные объекты относятся к памяти в сеанс Windows PowerShell. Этот шаг добавляет объекты для сетевого контроллера.

Следующий пример можно использовать для добавления настройке подсистемы балансировки нагрузки для сетевого контроллера.

    $lb = @{}
    $lb.ResourceId = $lbresourceid
    $lb.properties = $lbproperties

    $body = convertto-json $lb -Depth 100

    Invoke-WebRequest -Headers @{"Accept"="application/json"} -ContentType "application/json; charset=UTF-8" -Method "Put" -Uri "$uri/Networking/v1/loadbalancers/$lbresourceid" -Body $body -DisableKeepAlive -UseBasicParsing

После выполнения этого шага необходимо следовать в примере ниже, чтобы добавить к этому пулу внутренних сетевых интерфейсов.

## <a name="bkmk_obnat"></a>Пример: Использование SLB для исходящего NAT

Этот пример можно использовать для настройки SLB с пулом серверной части для предоставления исходящих возможность NAT для виртуальной Машины на пространство частных адресов виртуальной сети для достижения исходящих подключений к Интернету.

###<a name="step-1-create-the-loadbalancer-properties-front-end-ip-and-backend-pool"></a>Шаг 1: Создание свойства loadbalancer внешними IP и внутреннего пула.
Следующий пример можно использовать для создания свойств loadbalancer внешними IP и внутреннего пула.

    $lbresourceId = "OutboundNATMembers"
    $vipip = "10.127.132.7"

    $vipln = get-networkcontrollerlogicalnetwork -ConnectionUri $uri -resourceid "f8f67956-3906-4303-94c5-09cf91e7e311"

    $lbproperties = @{}
    $lbproperties.frontendipconfigurations = @()
    $lbproperties.backendAddressPools = @()
    $lbproperties.probes = @()
    $lbproperties.loadbalancingRules = @()
    $lbproperties.OutboundNatRules = @()

    $fe = @{}
    $fe.resourceId = "FE1"
    $fe.resourceRef = "/loadBalancers/$lbresourceId/frontendIPConfigurations/$($fe.resourceId)"
    $fe.properties = @{}
    $fe.properties.subnet = @{}
    $fe.properties.subnet.ResourceRef = $vipln.properties.Subnets[0].ResourceRef
    $fe.properties.privateIPAddress = $vipip
    $fe.properties.privateIPAllocationMethod = "Static"
    $lbproperties.frontendipconfigurations += $fe

    $backend = @{}
    $backend.resourceId = "BE1"
    $backend.resourceRef = "/loadBalancers/$lbresourceId/backendAddressPools/$($backend.resourceId)"
    $lbproperties.backendAddressPools += $backend

###<a name="step-2-define-the-outbound-nat-rule"></a>Шаг 2: Определение правила исходящей NAT
Следующий пример можно использовать для определения правило NAT для исходящих подключений. 

    $onat = @{}
    $onat.ResourceId = "onat1"
    $onat.properties = @{}
    $onat.properties.frontendipconfigurations = @()
    $onat.properties.frontendipconfigurations += $fe
    $onat.properties.backendaddresspool = $backend
    $onat.properties.protocol = "ALL"
    $lbproperties.OutboundNatRules += $onat

###<a name="step-3-add-the-load-balancer-object-in-network-controller"></a>Шаг 3: Добавление объекта подсистемы балансировки нагрузки в сетевого контроллера
Следующий пример можно использовать для добавления объект подсистемы балансировки нагрузки в сетевого контроллера.

    $lb = @{}
    $lb.ResourceId = $lbresourceid
    $lb.properties = $lbproperties

    $body = convertto-json $lb -Depth 100

    Invoke-WebRequest -Headers @{"Accept"="application/json"} -ContentType "application/json; charset=UTF-8" -Method "Put" -Uri "$uri/Networking/v1/loadbalancers/$lbresourceid" -Body $body -DisableKeepAlive -UseBasicParsing

На следующем шаге можно добавить сетевых интерфейсов, к которым вы хотите предоставить доступ к Интернету.

## <a name="bkmk_backend"></a>Пример: Добавление сетевых интерфейсов в пул серверной части
Этот пример можно использовать для добавления сетевых интерфейсов в пул серверной части.

Повторите этот шаг для каждого сетевого интерфейса, который может обрабатывать запросы проверки для виртуальных IP-адресов. Также можно повторить этот процесс на один сетевой интерфейс, чтобы добавить его к нескольким объектам подсистемы балансировки нагрузки. Например, если у вас есть объект подсистемы балансировки нагрузки для виртуальных IP-адресов веб-сервера и объект подсистемы балансировки нагрузки на отдельные для предоставления исходящих NAT.
    
### <a name="step-1-get-the-load-balancer-object-containing-the-back-end-pool-to-which-you-will-add-a-network-interface"></a>Шаг 1: Получите объект подсистемы балансировки нагрузки, содержащий пула серверной части, в которую вы добавите сетевого интерфейса
Следующий пример можно использовать для получения объекта подсистемы балансировки нагрузки.

    $lbresourceid = "LB2"
    $lb = (Invoke-WebRequest -Headers @{"Accept"="application/json"} -ContentType "application/json; charset=UTF-8" -Method "Get" -Uri "$uri/Networking/v1/loadbalancers/$lbresourceid" -DisableKeepAlive -UseBasicParsing).content | convertfrom-json 

### <a name="step-2-get-the-network-interface-and-add-the-backendaddress-pool-to-the-loadbalancerbackendaddresspools-array"></a>Шаг 2: Получение сетевого интерфейса и добавить пул backendaddress loadbalancerbackendaddresspools массива.
Следующий пример можно использовать для получения сетевого интерфейса и добавить пул backendaddress loadbalancerbackendaddresspools массива.

    $nic = get-networkcontrollernetworkinterface  -connectionuri $uri -resourceid 6daca142-7d94-0000-1111-c38c0141be06
    $nic.properties.IpConfigurations[0].properties.LoadBalancerBackendAddressPools += $lb.properties.backendaddresspools[0]
    
### <a name="step-3-put-the-network-interface-to-apply-the-change"></a>Шаг 3: Перевод сетевого интерфейса, чтобы применить изменения
Следующий пример можно использовать для размещения сетевой интерфейс, чтобы применить изменения.

    new-networkcontrollernetworkinterface  -connectionuri $uri -resourceid 6daca142-7d94-0000-1111-c38c0141be06 -properties $nic.properties -force
 
## <a name="bkmk_forward"></a>Пример: Использование подсистемы балансировки нагрузки программного обеспечения для пересылки трафика
Если вам нужно сопоставить виртуальный IP один сетевой интерфейс виртуальной сети без определения отдельных портов, можно создать правило пересылки уровня 3.  Это правило перенаправляет весь трафик от виртуальной Машины, через назначенные виртуальных IP-адресов, который должен находиться в объект PublicIPAddress.

Если виртуальных IP-адресов и DIP определены как той же подсети, затем это эквивалентно выполнению переадресации уровня 3 без NAT.

>[!NOTE]
>Этот процесс не требуется создать объект подсистемы балансировки нагрузки.  Назначение PublicIPAddress сетевой интерфейс является достаточно информации для подсистемы балансировки нагрузки программного обеспечения выполнить его настройку.

###<a name="step-1-create-a-public-ip-object-to-contain-the-vip"></a>Шаг 1: Создание общих объекта IP для хранения виртуальных IP-адресов
Следующий пример можно использовать для создания объекта общедоступных IP.

    $publicIPProperties = new-object Microsoft.Windows.NetworkController.PublicIpAddressProperties
    $publicIPProperties.ipaddress = "10.127.132.6"
    $publicIPProperties.PublicIPAllocationMethod = "static"
    $publicIPProperties.IdleTimeoutInMinutes = 4
    $publicIP = New-NetworkControllerPublicIpAddress -ResourceId "MyPIP" -Properties $publicIPProperties -ConnectionUri $uri

####<a name="step-2-assign-the-publicipaddress-to-a-network-interface"></a>Шаг 2: Присвоение PublicIPAddress к сетевому интерфейсу
Следующий пример можно использовать для назначения PublicIPAddress сетевого интерфейса.

    $nic = get-networkcontrollernetworkinterface  -connectionuri $uri -resourceid 6daca142-7d94-0000-1111-c38c0141be06
    $nic.properties.IpConfigurations[0].Properties.PublicIPAddress = $publicIP
    New-NetworkControllerNetworkInterface -ConnectionUri $uri -ResourceId $nic.ResourceId -Properties $nic.properties



 