---
title: Добавление виртуального шлюза в виртуальную сеть клиента
description: Сведения об использовании командлетов и скриптов Windows PowerShell для предоставления подключение сайт сайт для виртуальных сетей для вашего клиента.
manager: dougkim
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9552054-4eb9-48db-a6ce-f36ae55addcd
ms.author: pashort
author: shortpatti
ms.date: 08/23/2018
ms.openlocfilehash: b76019232be5091440c3e0cf5ad85569cbe0d4dc
ms.sourcegitcommit: 21165734a0f37c4cd702c275e85c9e7c42d6b3cb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2019
ms.locfileid: "65034480"
---
# <a name="add-a-virtual-gateway-to-a-tenant-virtual-network"></a>Добавление виртуального шлюза в виртуальную сеть клиента 

>Относится к: Windows Server (полугодовой канал), Windows Server 2016 

Сведения об использовании командлетов и скриптов Windows PowerShell для предоставления подключение сайт сайт для виртуальных сетей для вашего клиента. В этом разделе добавьте шлюзы виртуальной клиента к экземплярам шлюза RAS, которые являются членами пулов шлюзов с помощью сетевого контроллера. Шлюз RAS поддерживает до 100 клиентов, в зависимости от пропускной способности, необходимой для каждого клиента. Сетевой контроллер автоматически определяет наиболее шлюза RAS для использования при развертывании нового виртуального шлюза для клиентов.  

Каждый виртуальный шлюз соответствует от определенного клиента и состоит из одного или нескольких сетевых подключений (сеть сеть VPN-туннели) и, возможно, подключения протокола пограничного шлюза (BGP). Когда вы предоставите подключение сайт сайт, ваши клиенты могут подключить их виртуальной сети клиента к внешней сети, например корпоративной сети клиента, сети поставщика услуг или Интернет.
  
**Когда вы развертываете шлюз виртуальный клиента, у вас есть следующие параметры конфигурации:**  

| Параметры подключения к сети | Параметры конфигурации BGP  |
|---------|---------|
|<ul><li>IPSec — сеть виртуальной частной сети (VPN)</li><li>Универсальной инкапсуляции при маршрутизации (GRE)</li><li>Layer 3 forwarding (Пересылка третьего уровня)</li></ul>     |<ul><li>Конфигурация маршрутизатора BGP</li><li>Конфигурация узла BGP</li><li>Конфигурация политики маршрутизации BGP</li></ul>         |
---

Образцы скриптов Windows PowerShell и команды в этом разделе показано, как развернуть шлюз виртуальной клиента для шлюза RAS с каждым из этих вариантов.  
  
   
>[!IMPORTANT]  
>Перед выполнением любого из примеров команд Windows PowerShell и сценарии, приведенные значения всех переменных необходимо изменить таким образом, чтобы значения подходят для развертывания.  
  
1.  Убедитесь, что объект пула шлюза существует на сетевом контроллере. 

    ```PowerShell
    $uri = "https://ncrest.contoso.com"   
      
    # Retrieve the Gateway Pool configuration  
    $gwPool = Get-NetworkControllerGatewayPool -ConnectionUri $uri  
      
    # Display in JSON format  
    $gwPool | ConvertTo-Json -Depth 2   
     
    ```  

2.  Убедитесь, что подсеть, используемую для маршрутизации пакетов из виртуальной сети клиента существует на сетевом контроллере. Можно также получить виртуальную подсеть, используемая для маршрутизации между шлюзом клиента и виртуальной сети.  
  
    ```PowerShell 
    $uri = "https://ncrest.contoso.com"   
      
    # Retrieve the Tenant Virtual Network configuration  
    $Vnet = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri  -ResourceId "Contoso_Vnet1"   
      
    # Display in JSON format  
    $Vnet | ConvertTo-Json -Depth 4   
      
    # Retrieve the Tenant Virtual Subnet configuration  
    $RoutingSubnet = Get-NetworkControllerVirtualSubnet -ConnectionUri $uri  -ResourceId "Contoso_WebTier" -VirtualNetworkID $vnet.ResourceId   
      
    # Display in JSON format  
    $RoutingSubnet | ConvertTo-Json -Depth 4   
      
    ```  

3.  Создание объекта шлюза виртуальной клиента и затем обновить ссылку на пул шлюза.  Можно также указать виртуальную подсеть, используемая для маршрутизации между шлюзом и виртуальной сети.  После указания виртуальную подсеть вы обновите остальную часть свойств объекта виртуального шлюза, а затем добавьте новый виртуальный шлюз для клиента.
  
    ```PowerShell  
    # Create a new object for Tenant Virtual Gateway  
    $VirtualGWProperties = New-Object Microsoft.Windows.NetworkController.VirtualGatewayProperties   
      
    # Update Gateway Pool reference  
    $VirtualGWProperties.GatewayPools = @()   
    $VirtualGWProperties.GatewayPools += $gwPool   
      
    # Specify the Virtual Subnet that is to be used for routing between the gateway and Virtual Network   
    $VirtualGWProperties.GatewaySubnets = @()   
    $VirtualGWProperties.GatewaySubnets += $RoutingSubnet   
      
    # Update the rest of the Virtual Gateway object properties  
    $VirtualGWProperties.RoutingType = "Dynamic"   
    $VirtualGWProperties.NetworkConnections = @()   
    $VirtualGWProperties.BgpRouters = @()   
      
    # Add the new Virtual Gateway for tenant   
    $virtualGW = New-NetworkControllerVirtualGateway -ConnectionUri $uri  -ResourceId "Contoso_VirtualGW" -Properties $VirtualGWProperties -Force   
      
    ```  
  
4. Создание VPN-подключение сайт сайт с помощью IPsec, GRE, или слоя переадресации 3 (уровня 3).  

   >[!TIP]
   >При необходимости можно объединить все описанные выше действия и настроить виртуальный шлюз клиента со всеми параметрами подключения тремя.  Дополнительные сведения см. в разделе [настроить шлюз со всеми типами три подключения (IPsec, GRE, L3) и BGP](#optional-step-configure-a-gateway-with-all-three-connection-types-ipsec-gre-l3-and-bgp).
  
   **IPsec VPN-подключение сайт сайт**
  
   ```PowerShell  
   # Create a new object for Tenant Network Connection  
   $nwConnectionProperties = New-Object Microsoft.Windows.NetworkController.NetworkConnectionProperties   
  
   # Update the common object properties  
   $nwConnectionProperties.ConnectionType = "IPSec"   
   $nwConnectionProperties.OutboundKiloBitsPerSecond = 10000   
   $nwConnectionProperties.InboundKiloBitsPerSecond = 10000   
  
   # Update specific properties depending on the Connection Type  
   $nwConnectionProperties.IpSecConfiguration = New-Object Microsoft.Windows.NetworkController.IpSecConfiguration   
   $nwConnectionProperties.IpSecConfiguration.AuthenticationMethod = "PSK"   
   $nwConnectionProperties.IpSecConfiguration.SharedSecret = "P@ssw0rd"   
  
   $nwConnectionProperties.IpSecConfiguration.QuickMode = New-Object Microsoft.Windows.NetworkController.QuickMode   
   $nwConnectionProperties.IpSecConfiguration.QuickMode.PerfectForwardSecrecy = "PFS2048"   
   $nwConnectionProperties.IpSecConfiguration.QuickMode.AuthenticationTransformationConstant = "SHA256128"   
   $nwConnectionProperties.IpSecConfiguration.QuickMode.CipherTransformationConstant = "DES3"   
   $nwConnectionProperties.IpSecConfiguration.QuickMode.SALifeTimeSeconds = 1233   
   $nwConnectionProperties.IpSecConfiguration.QuickMode.IdleDisconnectSeconds = 500   
   $nwConnectionProperties.IpSecConfiguration.QuickMode.SALifeTimeKiloBytes = 2000   
  
   $nwConnectionProperties.IpSecConfiguration.MainMode = New-Object Microsoft.Windows.NetworkController.MainMode   
   $nwConnectionProperties.IpSecConfiguration.MainMode.DiffieHellmanGroup = "Group2"   
   $nwConnectionProperties.IpSecConfiguration.MainMode.IntegrityAlgorithm = "SHA256"   
   $nwConnectionProperties.IpSecConfiguration.MainMode.EncryptionAlgorithm = "AES256"   
   $nwConnectionProperties.IpSecConfiguration.MainMode.SALifeTimeSeconds = 1234   
   $nwConnectionProperties.IpSecConfiguration.MainMode.SALifeTimeKiloBytes = 2000   
  
   # L3 specific configuration (leave blank for IPSec)  
   $nwConnectionProperties.IPAddresses = @()   
   $nwConnectionProperties.PeerIPAddresses = @()   
  
   # Update the IPv4 Routes that are reachable over the site-to-site VPN Tunnel  
   $nwConnectionProperties.Routes = @()   
   $ipv4Route = New-Object Microsoft.Windows.NetworkController.RouteInfo   
   $ipv4Route.DestinationPrefix = "14.1.10.1/32"   
   $ipv4Route.metric = 10   
   $nwConnectionProperties.Routes += $ipv4Route   
  
   # Tunnel Destination (Remote Endpoint) Address  
   $nwConnectionProperties.DestinationIPAddress = "10.127.134.121"   
  
   # Add the new Network Connection for the tenant  
   New-NetworkControllerVirtualGatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId $virtualGW.ResourceId -ResourceId "Contoso_IPSecGW" -Properties $nwConnectionProperties -Force   
  
   ```  

   **GRE VPN-подключение сайт сайт**
  
   ```PowerShell  
   # Create a new object for the Tenant Network Connection  
   $nwConnectionProperties = New-Object Microsoft.Windows.NetworkController.NetworkConnectionProperties   
  
   # Update the common object properties  
   $nwConnectionProperties.ConnectionType = "GRE"   
   $nwConnectionProperties.OutboundKiloBitsPerSecond = 10000   
   $nwConnectionProperties.InboundKiloBitsPerSecond = 10000   
  
   # Update specific properties depending on the Connection Type  
   $nwConnectionProperties.GreConfiguration = New-Object Microsoft.Windows.NetworkController.GreConfiguration   
   $nwConnectionProperties.GreConfiguration.GreKey = 1234   
  
   # Update the IPv4 Routes that are reachable over the site-to-site VPN Tunnel  
   $nwConnectionProperties.Routes = @()   
   $ipv4Route = New-Object Microsoft.Windows.NetworkController.RouteInfo   
   $ipv4Route.DestinationPrefix = "14.2.20.1/32"   
   $ipv4Route.metric = 10   
   $nwConnectionProperties.Routes += $ipv4Route   
  
   # Tunnel Destination (Remote Endpoint) Address  
   $nwConnectionProperties.DestinationIPAddress = "10.127.134.122"   
  
   # L3 specific configuration (leave blank for GRE)  
   $nwConnectionProperties.L3Configuration = New-Object Microsoft.Windows.NetworkController.L3Configuration   
   $nwConnectionProperties.IPAddresses = @()   
   $nwConnectionProperties.PeerIPAddresses = @()   
  
   # Add the new Network Connection for the tenant  
   New-NetworkControllerVirtualGatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId $virtualGW.ResourceId -ResourceId "Contoso_GreGW" -Properties $nwConnectionProperties -Force   
  
   ```  

   **Переадресации L3 сетевого подключения**<p>
   Для уровня 3 сетевого подключения для правильной работы переадресации, необходимо настроить соответствующей логической сетью.   
  
   1. Настройте логическую сеть для L3 сетевого подключения переадресации.  <br>
  
      ```PowerShell  
      # Create a new object for the Logical Network to be used for L3 Forwarding  
      $lnProperties = New-Object Microsoft.Windows.NetworkController.LogicalNetworkProperties  
      
      $lnProperties.NetworkVirtualizationEnabled = $false  
      $lnProperties.Subnets = @()  
      
      # Create a new object for the Logical Subnet to be used for L3 Forwarding and update properties  
      $logicalsubnet = New-Object Microsoft.Windows.NetworkController.LogicalSubnet  
      $logicalsubnet.ResourceId = "Contoso_L3_Subnet"  
      $logicalsubnet.Properties = New-Object Microsoft.Windows.NetworkController.LogicalSubnetProperties  
      $logicalsubnet.Properties.VlanID = 1001  
      $logicalsubnet.Properties.AddressPrefix = "10.127.134.0/25"  
      $logicalsubnet.Properties.DefaultGateways = "10.127.134.1"  
      
      $lnProperties.Subnets += $logicalsubnet  
      
      # Add the new Logical Network to Network Controller  
      $vlanNetwork = New-NetworkControllerLogicalNetwork -ConnectionUri $uri -ResourceId "Contoso_L3_Network" -Properties $lnProperties -Force  
      
      ```  

   2. Создание сетевого подключения объекта JSON и добавьте его к сетевому контроллеру.  
  
      ```PowerShell 
      # Create a new object for the Tenant Network Connection  
      $nwConnectionProperties = New-Object Microsoft.Windows.NetworkController.NetworkConnectionProperties   
      
      # Update the common object properties  
      $nwConnectionProperties.ConnectionType = "L3"   
      $nwConnectionProperties.OutboundKiloBitsPerSecond = 10000   
      $nwConnectionProperties.InboundKiloBitsPerSecond = 10000   
      
      # GRE specific configuration (leave blank for L3)  
      $nwConnectionProperties.GreConfiguration = New-Object Microsoft.Windows.NetworkController.GreConfiguration   
      
      # Update specific properties depending on the Connection Type  
      $nwConnectionProperties.L3Configuration = New-Object Microsoft.Windows.NetworkController.L3Configuration   
      $nwConnectionProperties.L3Configuration.VlanSubnet = $vlanNetwork.properties.Subnets[0]   
      
      $nwConnectionProperties.IPAddresses = @()   
      $localIPAddress = New-Object Microsoft.Windows.NetworkController.CidrIPAddress   
      $localIPAddress.IPAddress = "10.127.134.55"   
      $localIPAddress.PrefixLength = 25   
      $nwConnectionProperties.IPAddresses += $localIPAddress   
      
      $nwConnectionProperties.PeerIPAddresses = @("10.127.134.65")   
      
      # Update the IPv4 Routes that are reachable over the site-to-site VPN Tunnel  
      $nwConnectionProperties.Routes = @()   
      $ipv4Route = New-Object Microsoft.Windows.NetworkController.RouteInfo   
      $ipv4Route.DestinationPrefix = "14.2.20.1/32"   
      $ipv4Route.metric = 10   
      $nwConnectionProperties.Routes += $ipv4Route   
      
      # Add the new Network Connection for the tenant  
      New-NetworkControllerVirtualGatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId $virtualGW.ResourceId -ResourceId "Contoso_L3GW" -Properties $nwConnectionProperties -Force   
      
      ```  
  
5. Настройка шлюза как маршрутизатор BGP и добавьте его к сетевому контроллеру. 
  
   1. Добавьте маршрутизатор BGP для клиента.  

      ```PowerShell  
      # Create a new object for the Tenant BGP Router  
      $bgpRouterproperties = New-Object Microsoft.Windows.NetworkController.VGwBgpRouterProperties   
      
      # Update the BGP Router properties  
      $bgpRouterproperties.ExtAsNumber = "0.64512"   
      $bgpRouterproperties.RouterId = "192.168.0.2"   
      $bgpRouterproperties.RouterIP = @("192.168.0.2")   
      
      # Add the new BGP Router for the tenant  
      $bgpRouter = New-NetworkControllerVirtualGatewayBgpRouter -ConnectionUri $uri -VirtualGatewayId $virtualGW.ResourceId -ResourceId "Contoso_BgpRouter1" -Properties $bgpRouterProperties -Force   
      
      ```  

   2. Добавление узла BGP для этого клиента, относящиеся к соединению сеть-сеть VPN, добавленных выше.  
  
      ```PowerShell
      # Create a new object for Tenant BGP Peer  
      $bgpPeerProperties = New-Object Microsoft.Windows.NetworkController.VGwBgpPeerProperties   
      
      # Update the BGP Peer properties  
      $bgpPeerProperties.PeerIpAddress = "14.1.10.1"   
      $bgpPeerProperties.AsNumber = 64521   
      $bgpPeerProperties.ExtAsNumber = "0.64521"   
      
      # Add the new BGP Peer for tenant  
      New-NetworkControllerVirtualGatewayBgpPeer -ConnectionUri $uri -VirtualGatewayId $virtualGW.ResourceId -BgpRouterName $bgpRouter.ResourceId -ResourceId "Contoso_IPSec_Peer" -Properties $bgpPeerProperties -Force   
      
      ```  

## <a name="optional-step-configure-a-gateway-with-all-three-connection-types-ipsec-gre-l3-and-bgp"></a>(Необязательно) Настройка шлюза со всеми типами три подключения (IPsec, GRE, L3) и BGP  
При необходимости можно объединить все предыдущие шаги и настроить виртуальный шлюз клиента со всеми параметрами подключения тремя:   
  
```PowerShell  
# Create a new Virtual Gateway Properties type object  
$VirtualGWProperties = New-Object Microsoft.Windows.NetworkController.VirtualGatewayProperties  
  
# Update GatewayPool reference  
$VirtualGWProperties.GatewayPools = @()  
$VirtualGWProperties.GatewayPools += $gwPool  
  
# Specify the Virtual Subnet that is to be used for routing between GW and VNET  
$VirtualGWProperties.GatewaySubnets = @()  
$VirtualGWProperties.GatewaySubnets += $RoutingSubnet  
  
# Update some basic properties  
$VirtualGWProperties.RoutingType = "Dynamic"  
  
# Update Network Connection object(s)  
$VirtualGWProperties.NetworkConnections = @()  
  
# IPSec Connection configuration  
$ipSecConnection = New-Object Microsoft.Windows.NetworkController.NetworkConnection  
$ipSecConnection.ResourceId = "Contoso_IPSecGW"  
$ipSecConnection.Properties = New-Object Microsoft.Windows.NetworkController.NetworkConnectionProperties  
$ipSecConnection.Properties.ConnectionType = "IPSec"  
$ipSecConnection.Properties.OutboundKiloBitsPerSecond = 10000  
$ipSecConnection.Properties.InboundKiloBitsPerSecond = 10000  
  
$ipSecConnection.Properties.IpSecConfiguration = New-Object Microsoft.Windows.NetworkController.IpSecConfiguration  
  
$ipSecConnection.Properties.IpSecConfiguration.AuthenticationMethod = "PSK"  
$ipSecConnection.Properties.IpSecConfiguration.SharedSecret = "P@ssw0rd"  
  
$ipSecConnection.Properties.IpSecConfiguration.QuickMode = New-Object Microsoft.Windows.NetworkController.QuickMode  
  
$ipSecConnection.Properties.IpSecConfiguration.QuickMode.PerfectForwardSecrecy = "PFS2048"  
$ipSecConnection.Properties.IpSecConfiguration.QuickMode.AuthenticationTransformationConstant = "SHA256128"  
$ipSecConnection.Properties.IpSecConfiguration.QuickMode.CipherTransformationConstant = "DES3"  
$ipSecConnection.Properties.IpSecConfiguration.QuickMode.SALifeTimeSeconds = 1233  
$ipSecConnection.Properties.IpSecConfiguration.QuickMode.IdleDisconnectSeconds = 500  
$ipSecConnection.Properties.IpSecConfiguration.QuickMode.SALifeTimeKiloBytes = 2000  
  
$ipSecConnection.Properties.IpSecConfiguration.MainMode = New-Object Microsoft.Windows.NetworkController.MainMode  
  
$ipSecConnection.Properties.IpSecConfiguration.MainMode.DiffieHellmanGroup = "Group2"  
$ipSecConnection.Properties.IpSecConfiguration.MainMode.IntegrityAlgorithm = "SHA256"  
$ipSecConnection.Properties.IpSecConfiguration.MainMode.EncryptionAlgorithm = "AES256"  
$ipSecConnection.Properties.IpSecConfiguration.MainMode.SALifeTimeSeconds = 1234  
$ipSecConnection.Properties.IpSecConfiguration.MainMode.SALifeTimeKiloBytes = 2000  
  
$ipSecConnection.Properties.IPAddresses = @()  
$ipSecConnection.Properties.PeerIPAddresses = @()  
  
$ipSecConnection.Properties.Routes = @()  
  
$ipv4Route = New-Object Microsoft.Windows.NetworkController.RouteInfo  
$ipv4Route.DestinationPrefix = "14.1.10.1/32"  
$ipv4Route.metric = 10  
$ipSecConnection.Properties.Routes += $ipv4Route  
  
$ipSecConnection.Properties.DestinationIPAddress = "10.127.134.121"  
  
# GRE Connection configuration  
$greConnection = New-Object Microsoft.Windows.NetworkController.NetworkConnection  
$greConnection.ResourceId = "Contoso_GreGW"  
  
$greConnection.Properties = New-Object Microsoft.Windows.NetworkController.NetworkConnectionProperties  
$greConnection.Properties.ConnectionType = "GRE"  
$greConnection.Properties.OutboundKiloBitsPerSecond = 10000  
$greConnection.Properties.InboundKiloBitsPerSecond = 10000  
  
$greConnection.Properties.GreConfiguration = New-Object Microsoft.Windows.NetworkController.GreConfiguration  
$greConnection.Properties.GreConfiguration.GreKey = 1234  
  
$greConnection.Properties.IPAddresses = @()  
$greConnection.Properties.PeerIPAddresses = @()  
  
$greConnection.Properties.Routes = @()  
  
$ipv4Route = New-Object Microsoft.Windows.NetworkController.RouteInfo  
$ipv4Route.DestinationPrefix = "14.2.20.1/32"  
$ipv4Route.metric = 10  
$greConnection.Properties.Routes += $ipv4Route  
  
$greConnection.Properties.DestinationIPAddress = "10.127.134.122"  
  
$greConnection.Properties.L3Configuration = New-Object Microsoft.Windows.NetworkController.L3Configuration  
  
# L3 Forwarding connection configuration  
$l3Connection = New-Object Microsoft.Windows.NetworkController.NetworkConnection  
$l3Connection.ResourceId = "Contoso_L3GW"  
  
$l3Connection.Properties = New-Object Microsoft.Windows.NetworkController.NetworkConnectionProperties  
$l3Connection.Properties.ConnectionType = "L3"  
$l3Connection.Properties.OutboundKiloBitsPerSecond = 10000  
$l3Connection.Properties.InboundKiloBitsPerSecond = 10000  
  
$l3Connection.Properties.GreConfiguration = New-Object Microsoft.Windows.NetworkController.GreConfiguration  
$l3Connection.Properties.L3Configuration = New-Object Microsoft.Windows.NetworkController.L3Configuration  
$l3Connection.Properties.L3Configuration.VlanSubnet = $vlanNetwork.properties.Subnets[0]  
  
$l3Connection.Properties.IPAddresses = @()  
$localIPAddress = New-Object Microsoft.Windows.NetworkController.CidrIPAddress  
$localIPAddress.IPAddress = "10.127.134.55"  
$localIPAddress.PrefixLength = 25  
$l3Connection.Properties.IPAddresses += $localIPAddress  
  
$l3Connection.Properties.PeerIPAddresses = @("10.127.134.65")  
  
$l3Connection.Properties.Routes = @()  
$ipv4Route = New-Object Microsoft.Windows.NetworkController.RouteInfo  
$ipv4Route.DestinationPrefix = "14.2.20.1/32"  
$ipv4Route.metric = 10  
$l3Connection.Properties.Routes += $ipv4Route  
  
# Update BGP Router Object  
$VirtualGWProperties.BgpRouters = @()  
  
$bgpRouter = New-Object Microsoft.Windows.NetworkController.VGwBgpRouter  
$bgpRouter.ResourceId = "Contoso_BgpRouter1"  
$bgpRouter.Properties = New-Object Microsoft.Windows.NetworkController.VGwBgpRouterProperties  
  
$bgpRouter.Properties.ExtAsNumber = "0.64512"  
$bgpRouter.Properties.RouterId = "192.168.0.2"  
$bgpRouter.Properties.RouterIP = @("192.168.0.2")  
  
$bgpRouter.Properties.BgpPeers = @()  
  
# Create BGP Peer Object(s)  
# BGP Peer for IPSec Connection  
$bgpPeer_IPSec = New-Object Microsoft.Windows.NetworkController.VGwBgpPeer  
$bgpPeer_IPSec.ResourceId = "Contoso_IPSec_Peer"  
  
$bgpPeer_IPSec.Properties = New-Object Microsoft.Windows.NetworkController.VGwBgpPeerProperties  
$bgpPeer_IPSec.Properties.PeerIpAddress = "14.1.10.1"  
$bgpPeer_IPSec.Properties.AsNumber = 64521  
$bgpPeer_IPSec.Properties.ExtAsNumber = "0.64521"  
  
$bgpRouter.Properties.BgpPeers += $bgpPeer_IPSec  
  
# BGP Peer for GRE Connection  
$bgpPeer_Gre = New-Object Microsoft.Windows.NetworkController.VGwBgpPeer  
$bgpPeer_Gre.ResourceId = "Contoso_Gre_Peer"  
  
$bgpPeer_Gre.Properties = New-Object Microsoft.Windows.NetworkController.VGwBgpPeerProperties  
$bgpPeer_Gre.Properties.PeerIpAddress = "14.2.20.1"  
$bgpPeer_Gre.Properties.AsNumber = 64522  
$bgpPeer_Gre.Properties.ExtAsNumber = "0.64522"  
  
$bgpRouter.Properties.BgpPeers += $bgpPeer_Gre  
  
# BGP Peer for L3 Connection  
$bgpPeer_L3 = New-Object Microsoft.Windows.NetworkController.VGwBgpPeer  
$bgpPeer_L3.ResourceId = "Contoso_L3_Peer"  
  
$bgpPeer_L3.Properties = New-Object Microsoft.Windows.NetworkController.VGwBgpPeerProperties  
$bgpPeer_L3.Properties.PeerIpAddress = "14.3.30.1"  
$bgpPeer_L3.Properties.AsNumber = 64523  
$bgpPeer_L3.Properties.ExtAsNumber = "0.64523"  
  
$bgpRouter.Properties.BgpPeers += $bgpPeer_L3  
  
$VirtualGWProperties.BgpRouters += $bgpRouter  
  
# Finally Add the new Virtual Gateway for tenant  
New-NetworkControllerVirtualGateway -ConnectionUri $uri  -ResourceId "Contoso_VirtualGW" -Properties $VirtualGWProperties -Force  
  
```  

## <a name="modify-a-gateway-for-a-virtual-network"></a>Изменить шлюз для виртуальной сети  

  
**Извлеките конфигурацию для компонента и сохранить его в переменной**

```PowerShell  
$nwConnection = Get-NetworkControllerVirtualGatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId "Contoso_VirtualGW" -ResourceId "Contoso_IPSecGW"  
```  

**Навигации по структуре переменной для охвата обязательное свойство и ему присвоено значение обновлений**
  
```PowerShell  
$nwConnection.properties.IpSecConfiguration.SharedSecret = "C0mplexP@ssW0rd"  
```  

**Добавьте измененную конфигурацию для замены предыдущих версиях конфигурации на сетевом контроллере**
 
```PowerShell  
New-NetworkControllerVirtualGatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId "Contoso_VirtualGW" -ResourceId $nwConnection.ResourceId -Properties $nwConnection.Properties -Force  
```  


## <a name="remove-a-gateway-from-a-virtual-network"></a>Удаление шлюза из виртуальной сети 
Чтобы удалить шлюз отдельных компонентов или всего шлюза можно использовать следующие команды Windows PowerShell.  

**Удаление сетевого подключения**  
```PowerShell  
Remove-NetworkControllerVirtualGatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId "Contoso_VirtualGW" -ResourceId "Contoso_IPSecGW" -Force  
```  

**Удаление узла BGP** 
```PowerShell  
Remove-NetworkControllerVirtualGatewayBgpPeer -ConnectionUri $uri -VirtualGatewayId "Contoso_VirtualGW" -BgpRouterName "Contoso_BgpRouter1" -ResourceId "Contoso_IPSec_Peer" -Force  
```  

**Удалить маршрутизатор BGP**
```PowerShell  
Remove-NetworkControllerVirtualGatewayBgpRouter -ConnectionUri $uri -VirtualGatewayId "Contoso_VirtualGW" -ResourceId "Contoso_BgpRouter1" -Force  
```

**Удаление шлюза**  
```PowerShell  
Remove-NetworkControllerVirtualGateway -ConnectionUri $uri -ResourceId "Contoso_VirtualGW" -Force   
```  

---