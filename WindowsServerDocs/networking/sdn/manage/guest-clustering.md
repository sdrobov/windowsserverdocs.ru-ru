---
title: Кластеризация гостевых систем в виртуальной сети
description: Виртуальные машины, подключенные к виртуальной сети могут использовать только IP-адреса, назначенные сетевого контроллера для связи по сети.  Технологии кластеризации, которым необходим плавающего IP-адреса, например Microsoft отказоустойчивой кластеризации, требуют некоторых дополнительных шагов для правильного функционирования.
manager: dougkim
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
ms.date: 08/26/2018
ms.openlocfilehash: 97c20fd07d06b609686daf4d6308a9f248873036
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66446340"
---
# <a name="guest-clustering-in-a-virtual-network"></a>Кластеризация гостевых систем в виртуальной сети

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Виртуальные машины, подключенные к виртуальной сети могут использовать только IP-адреса, назначенные сетевого контроллера для связи по сети.  Технологии кластеризации, которым необходим плавающего IP-адреса, например Microsoft отказоустойчивой кластеризации, требуют некоторых дополнительных шагов для правильного функционирования.

Метод делающий доступными плавающий IP-адрес является использование программной подсистемы балансировки нагрузки \(SLB\) виртуальный IP-адрес \(виртуальный IP-адрес\).  Таким образом, чтобы программный балансировщик Нагрузки направляет трафик на компьютере, на котором в данный момент этот IP-адрес подсистемы балансировки нагрузки должны быть настроены пробу работоспособности на порте, на этот IP-адрес.


## <a name="example-load-balancer-configuration"></a>Пример. Конфигурация подсистемы балансировки нагрузки

В этом примере предполагается, что вы уже создали виртуальных машин, которые станут узлами кластера и применения их к виртуальной сети.  Инструкции см. в разделе [Создание виртуальной Машины и подключение к виртуальной сети клиента или виртуальной локальной сети](https://technet.microsoft.com/windows-server-docs/networking/sdn/manage/create-a-tenant-vm).  

В этом примере будет создать виртуальный IP-адрес (192.168.2.100) для представления с плавающей запятой IP-адрес кластера и настроить пробу работоспособности для наблюдения за TCP-порта 59999, чтобы определить, какой узел является активным.

1. Выберите виртуальный IP-адрес.<p>Подготовка, назначив Виртуальный IP-адрес, который может быть любой неиспользуемый или зарезервированный адрес, в той же подсети, где размещаются узлы кластера.  Виртуальный IP-адрес должен соответствовать с плавающей запятой адрес кластера.

   ```PowerShell
   $VIP = "192.168.2.100"
   $subnet = "Subnet2"
   $VirtualNetwork = "MyNetwork"
   $ResourceId = "MyNetwork_InternalVIP"
   ```

2. Создайте объект свойства подсистемы балансировки нагрузки.

   ```PowerShell
   $LoadBalancerProperties = new-object Microsoft.Windows.NetworkController.LoadBalancerProperties
   ```

3. Создание внешнего\-конечный IP-адрес.

   ```PowerShell
   $LoadBalancerProperties.frontendipconfigurations += $FrontEnd = new-object Microsoft.Windows.NetworkController.LoadBalancerFrontendIpConfiguration
   $FrontEnd.properties = new-object Microsoft.Windows.NetworkController.LoadBalancerFrontendIpConfigurationProperties
   $FrontEnd.resourceId = "Frontend1"
   $FrontEnd.resourceRef = "/loadBalancers/$ResourceId/frontendIPConfigurations/$($FrontEnd.resourceId)"
   $FrontEnd.properties.subnet = new-object Microsoft.Windows.NetworkController.Subnet
   $FrontEnd.properties.subnet.ResourceRef = "/VirtualNetworks/MyNetwork/Subnets/Subnet2"
   $FrontEnd.properties.privateIPAddress = $VIP
   $FrontEnd.properties.privateIPAllocationMethod = "Static"
   ```

4. Создание копирования\-завершить пул должен содержать узлы кластера.

   ```PowerShell
   $BackEnd = new-object Microsoft.Windows.NetworkController.LoadBalancerBackendAddressPool
   $BackEnd.properties = new-object Microsoft.Windows.NetworkController.LoadBalancerBackendAddressPoolProperties
   $BackEnd.resourceId = "Backend1"
   $BackEnd.resourceRef = "/loadBalancers/$ResourceId/backendAddressPools/$($BackEnd.resourceId)"
   $LoadBalancerProperties.backendAddressPools += $BackEnd
   ```

5. Добавление проверки для определения узла кластера, где плавающего адреса неактивная на текущий момент. 

   >[!NOTE]
   >Запрос проверки постоянный адрес виртуальной Машины на порте, см. ниже.  Порт должен отвечать только на активном узле. 

   ```PowerShell
   $LoadBalancerProperties.probes += $lbprobe = new-object Microsoft.Windows.NetworkController.LoadBalancerProbe
   $lbprobe.properties = new-object Microsoft.Windows.NetworkController.LoadBalancerProbeProperties

   $lbprobe.ResourceId = "Probe1"
   $lbprobe.resourceRef = "/loadBalancers/$ResourceId/Probes/$($lbprobe.resourceId)"
   $lbprobe.properties.protocol = "TCP"
   $lbprobe.properties.port = "59999"
   $lbprobe.properties.IntervalInSeconds = 5
   $lbprobe.properties.NumberOfProbes = 11
   ```

6. Добавление правила балансировки нагрузки для TCP-порт 1433.<p>Протокол и порт, при необходимости можно изменить.  Также можно повторить этот шаг несколько раз для другие порты и protcols на этот виртуальный IP-адрес.  Очень важно, что EnableFloatingIP установлено значение $true, так как это означает, что подсистемы балансировки нагрузки для отправки пакета на узел с помощью исходного виртуального IP-адреса на месте.

   ```PowerShell
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
   ```

7. Создание подсистемы балансировки нагрузки на сетевом контроллере.

   ```PowerShell
   $lb = New-NetworkControllerLoadBalancer -ConnectionUri $URI -ResourceId $ResourceId -Properties $LoadBalancerProperties -Force
   ```

8. Добавление узлов кластера во внутренний пул.<p>Можно добавить столько узлов для пула, сколько требуется для кластера.

   ```PowerShell
   # Cluster Node 1

   $nic = get-networkcontrollernetworkinterface  -connectionuri $uri -resourceid "ClusterNode1_Network-Adapter"
   $nic.properties.IpConfigurations[0].properties.LoadBalancerBackendAddressPools += $lb.properties.backendaddresspools[0]
   $nic = new-networkcontrollernetworkinterface  -connectionuri $uri -resourceid $nic.resourceid -properties $nic.properties -force

    # Cluster Node 2

   $nic = get-networkcontrollernetworkinterface  -connectionuri $uri -resourceid "ClusterNode2_Network-Adapter"
   $nic.properties.IpConfigurations[0].properties.LoadBalancerBackendAddressPools += $lb.properties.backendaddresspools[0]
   $nic = new-networkcontrollernetworkinterface  -connectionuri $uri -resourceid $nic.resourceid -properties $nic.properties -force
   ```

   После создания подсистемы балансировки нагрузки и добавить сетевые интерфейсы во внутренний пул, все готово для настройки кластера.  

9. (Необязательно) Если вы используете Microsoft отказоустойчивого кластера, по-прежнему в следующем примере. 

## <a name="example-2-configuring-a-microsoft-failover-cluster"></a>Пример 2: Настройка отказоустойчивого кластера Майкрософт

Чтобы настроить отказоустойчивый кластер, можно использовать следующие действия.

1. Установите и настройте свойства для отказоустойчивого кластера.

   ```PowerShell
   add-windowsfeature failover-clustering -IncludeManagementTools
   Import-module failoverclusters

   $ClusterName = "MyCluster"
   
   $ClusterNetworkName = "Cluster Network 1"
   $IPResourceName =  
   $ILBIP = “192.168.2.100” 

   $nodes = @("DB1", "DB2")
   ```

2. Создайте кластер на одном узле.

   ```PowerShell
   New-Cluster -Name $ClusterName -NoStorage -Node $nodes[0]
   ```

3. Остановите ресурс кластера.

   ```PowerShell
   Stop-ClusterResource "Cluster Name" 
   ```

4. Установка кластера IP-адрес и порта пробы.<p>IP-адрес должен совпадать с адресом внешний IP-адрес, используемый в предыдущем примере, и порт пробы должен совпадать с портом пробы в предыдущем примере.

   ```PowerShell
   Get-ClusterResource "Cluster IP Address" | Set-ClusterParameter -Multiple @{"Address"="$ILBIP";"ProbePort"="59999";"SubnetMask"="255.255.255.255";"Network"="$ClusterNetworkName";"EnableDhcp"=0}
   ```

5. Запустите ресурсы кластера.

   ```PowerShell
    Start-ClusterResource "Cluster IP Address"  -Wait 60 
    Start-ClusterResource "Cluster Name"  -Wait 60 
   ```

6. Добавьте оставшиеся узлы.

   ```PowerShell
   Add-ClusterNode $nodes[1]
   ```

_**Кластера активен.** _ Трафик, идущий в виртуальный IP-адрес для указанного порта направлена на активном узле.

---