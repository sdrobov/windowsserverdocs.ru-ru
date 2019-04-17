---
title: Гостевой кластер в виртуальной сети
description: Этот раздел является частью программного обеспечения определены сетевые руководство о том, как управление рабочими нагрузками клиента и виртуальные сети в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e9e5c81-aa61-479e-abaf-64c5e95f90dc
ms.author: grcusanz
author: shortpatti
ms.openlocfilehash: 5cab7e7c0ca0af848b4b58362388701cc4357860
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="guest-clustering-in-a-virtual-network"></a>Гостевой кластер в виртуальной сети

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Только виртуальных машин, подключенных к виртуальной сети могут использовать IP-адреса, назначенные сетевого контроллера для связи по сети.  Это означает, что кластеризации технологии, которые требуют значений с плавающей IP-адрес, например отказоустойчивый кластер корпорации Майкрософт, для правильной работы требуется выполнить несколько дополнительных действий.

Метод для выбора доступны с плавающей IP-адресов является использование \(SLB\) программного балансировщика нагрузки виртуальный IP-\(VIP\).  Балансировка нагрузки программного обеспечения должны быть настроены проверка индекса на порта, IP-адресов, чтобы SLB будет направлять трафик на компьютере, который в данный момент находится IP.

## <a name="example-load-balancer-configuration"></a>Пример: Конфигурации подсистемы балансировки нагрузки

В этом примере предполагается, что вы уже создали виртуальные машины, которые станут узлов кластера и назначенные виртуальной сети.  Инструкции см. в разделе [создания виртуальной Машины и подключение к виртуальной сети клиента или виртуальной локальной сети](https://technet.microsoft.com/windows-server-docs/networking/sdn/manage/create-a-tenant-vm).  

В этом примере будет создать виртуальный IP-адрес (192.168.2.100) для представления с плавающей IP-адрес кластера и настройте проверка индекса для наблюдения за TCP-порт 59999, чтобы определить, какой узел является активной.

### <a name="step-1-select-the-vip"></a>Шаг 1: Выберите виртуальных IP-адресов
Подготовка, назначив виртуальных IP-адресов IP-адрес.  Этот адрес может быть все неиспользуемые или зарезервированные адреса в той же подсети, что и узлы кластера.  VIP должен совпадать с плавающей адресом кластера.

    $VIP = "192.168.2.100"
    $subnet = "Subnet2"
    $VirtualNetwork = "MyNetwork"
    $ResourceId = "MyNetwork_InternalVIP"

### <a name="step-2-create-the-load-balancer-properties-object"></a>Шаг 2: Создание объект свойств подсистемы балансировки нагрузки

Следующий пример команды можно использовать для создания объекта свойства подсистемы балансировки нагрузки.

    $LoadBalancerProperties = new-object Microsoft.Windows.NetworkController.LoadBalancerProperties

### <a name="step-3-create-a-front-end-ip-address"></a>Шаг 3: Создание front\ конечный IP-адрес

Следующий пример команды можно использовать для создания front\ конечный IP-адрес.

    $LoadBalancerProperties.frontendipconfigurations += $FrontEnd = new-object Microsoft.Windows.NetworkController.LoadBalancerFrontendIpConfiguration
    $FrontEnd.properties = new-object Microsoft.Windows.NetworkController.LoadBalancerFrontendIpConfigurationProperties
    $FrontEnd.resourceId = "Frontend1"
    $FrontEnd.resourceRef = "/loadBalancers/$ResourceId/frontendIPConfigurations/$($FrontEnd.resourceId)"
    $FrontEnd.properties.subnet = new-object Microsoft.Windows.NetworkController.Subnet
    $FrontEnd.properties.subnet.ResourceRef = "/VirtualNetworks/MyNetwork/Subnets/Subnet2"
    $FrontEnd.properties.privateIPAddress = $VIP
    $FrontEnd.properties.privateIPAllocationMethod = "Static"

### <a name="step-4-create-a-back-end-pool-to-contain-the-cluster-nodes"></a>Шаг 4: Создание пула back\ окончания может содержать узлы кластера

Следующий пример команды можно использовать для создания пула back\ end

    $BackEnd = new-object Microsoft.Windows.NetworkController.LoadBalancerBackendAddressPool
    $BackEnd.properties = new-object Microsoft.Windows.NetworkController.LoadBalancerBackendAddressPoolProperties
    $BackEnd.resourceId = "Backend1"
    $BackEnd.resourceRef = "/loadBalancers/$ResourceId/backendAddressPools/$($BackEnd.resourceId)"
    $LoadBalancerProperties.backendAddressPools += $BackEnd

### <a name="step-5-add-a-probe"></a>Шаг 5: Добавление зондирования
Проба необходимые для определения какие плавающей адрес в данный момент на узле кластера.

>[!NOTE]
>Запрос проверки постоянный адрес виртуальной Машины на порт, определенный ниже.  Порт должен отвечать только на активном узле. 

    $LoadBalancerProperties.probes += $lbprobe = new-object Microsoft.Windows.NetworkController.LoadBalancerProbe
    $lbprobe.properties = new-object Microsoft.Windows.NetworkController.LoadBalancerProbeProperties

    $lbprobe.ResourceId = "Probe1"
    $lbprobe.resourceRef = "/loadBalancers/$ResourceId/Probes/$($lbprobe.resourceId)"
    $lbprobe.properties.protocol = "TCP"
    $lbprobe.properties.port = "59999"
    $lbprobe.properties.IntervalInSeconds = 5
    $lbprobe.properties.NumberOfProbes = 11

### <a name="step-5-add-the-load-balancing-rules"></a>Шаг 5: Добавление правила балансировки нагрузки
На этом этапе создается правило для порта TCP 1433 балансировки нагрузки.  Протокол и порт, при необходимости можно изменить.  Также можно повторить этот шаг несколько раз для дополнительные порты и протоколы, на этом виртуальных IP-адресов.  Очень важно, что EnableFloatingIP задано значение $true, поскольку это значение определяет подсистемы балансировки нагрузки для отправки пакета на узел с исходной виртуальных IP-адресов на месте.

    $LoadBalancerProperties.loadbalancingRules += $lbrule = new-object Microsoft.Windows.NetworkController.LoadBalancingRule
    $lbrule.properties = new-object Microsoft.Windows.NetworkController.LoadBalancingRuleProperties
    $lbrule.ResourceId = "Rules1"

    $lbrule.properties.frontendipconfigurations += $FrontEnd
    $lbrule.properties.backendaddresspool = $BackEnd 
    $lbrule.properties.protocol = "TCP"
    $lbrule.properties.frontendPort = $lbrule.properties.backendPort = 1433 
    $lbrule.properties.IdleTimeoutInMinutes = 4
    $lbrule.properties.EnableFloatingIP = $true
    $lbrule.properties.Probe = $lbprobe

### <a name="step-5-create-the-load-balancer-in-network-controller"></a>Шаг 5: Создание подсистемы балансировки нагрузки в сетевого контроллера

Следующий пример команды можно использовать для создания подсистемы балансировки нагрузки.

    $lb = New-NetworkControllerLoadBalancer -ConnectionUri $URI -ResourceId $ResourceId -Properties $LoadBalancerProperties -Force

### <a name="step-6-add-the-cluster-nodes-to-the-backend-pool"></a>Шаг 6: Добавление узлов кластера в пул серверная часть

В этом примере показано добавление двух участников группы, но можно добавить в пул столько узлов, сколько требуется для кластера.

    # Cluster Node 1

    $nic = get-networkcontrollernetworkinterface  -connectionuri $uri -resourceid "ClusterNode1_Network-Adapter"
    $nic.properties.IpConfigurations[0].properties.LoadBalancerBackendAddressPools += $lb.properties.backendaddresspools[0]
    $nic = new-networkcontrollernetworkinterface  -connectionuri $uri -resourceid $nic.resourceid -properties $nic.properties -force

    # Cluster Node 2

    $nic = get-networkcontrollernetworkinterface  -connectionuri $uri -resourceid "ClusterNode2_Network-Adapter"
    $nic.properties.IpConfigurations[0].properties.LoadBalancerBackendAddressPools += $lb.properties.backendaddresspools[0]
    $nic = new-networkcontrollernetworkinterface  -connectionuri $uri -resourceid $nic.resourceid -properties $nic.properties -force

Как только вы создали подсистемы балансировки нагрузки и добавлены в пул внутренних сетевых интерфейсов, вы будете готовы настроить кластер.  Если вы используете Microsoft отказоустойчивый кластер, можно продолжить в следующем примере. 

## <a name="example-2-configuring-a-microsoft-failover-cluster"></a>Пример 2: Настройка отказоустойчивого кластера Майкрософт

Для настройки отказоустойчивого кластера можно использовать следующие действия.

### <a name="step-1-install-failover-clustering"></a>Шаг 1: Установка отказоустойчивой кластеризации

Установка и настройка свойств для отказоустойчивого кластера можно использовать команды в следующем примере.

    add-windowsfeature failover-clustering -IncludeManagementTools
    Import-module failoverclusters

    $ClusterName = "MyCluster"
   
    $ClusterNetworkName = "Cluster Network 1"
    $IPResourceName =  
    $ILBIP = “192.168.2.100” 

    $nodes = @("DB1", "DB2")

### <a name="step-2-create-the-cluster-on-one-node"></a>Шаг 2: Создание кластера на одном узле

Следующий пример команды можно использовать для создания кластера на узле.

    New-Cluster -Name $ClusterName -NoStorage -Node $nodes[0]

### <a name="step-3-stop-the-cluster-resource"></a>Шаг 3: Остановки ресурса кластера

Следующий пример команды можно использовать для остановки ресурса кластера.

    Stop-ClusterResource "Cluster Name" 

### <a name="step-4-set-the-cluster-ip-and-probe-port"></a>Шаг 4: Установка кластера IP-адрес и Проверка порта
IP-адрес должен соответствовать переднего плана IP-адрес, используемый в предыдущем примере и порт пробы должен совпадать с номером порта проверки в предыдущем примере.

    Get-ClusterResource "Cluster IP Address" | Set-ClusterParameter -Multiple @{"Address"="$ILBIP";"ProbePort"="59999";"SubnetMask"="255.255.255.255";"Network"="$ClusterNetworkName";"EnableDhcp"=0}

### <a name="step-5-start-the-cluster-resources"></a>Шаг 5: Запустите ресурсов кластера

Следующий пример команды можно использовать для запуска ресурсов кластера.

    Start-ClusterResource "Cluster IP Address"  -Wait 60 
    Start-ClusterResource "Cluster Name"  -Wait 60 

### <a name="step-6-add-the-remaining-nodes"></a>Шаг 6: Добавление остальные узлы

Следующий пример команды можно использовать для добавления узлов кластера.

    Add-ClusterNode $nodes[1]

После завершения выполнения последнего шага кластера является активной. Трафика виртуальных IP-адресов на указанный порт будут направляться на активный узел.