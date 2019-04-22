---
title: Настройка пиринга виртуальной сети
description: Настройка пиринга виртуальных сетей включает в себя создание двух виртуальных сетей, получить пиринговой связи.
manager: dougkim
ms.prod: windows-server-threshold
ms.technology: networking-hv-switch
ms.topic: get-started-article
ms.assetid: ''
ms.author: pashort
author: shortpatti
ms.date: 08/08/2018
ms.openlocfilehash: 3ef3db879080e3372e7b287dcc55ae052c1fe109
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59816395"
---
# <a name="configure-virtual-network-peering"></a>Настройка пиринга виртуальной сети

>Относится к: Windows Server

В этой процедуре используется Windows PowerShell для создания двух виртуальных сетей, каждый с одной подсетью. Затем настроить пиринг между двумя виртуальными сетями, чтобы обеспечить подключение между ними.

- [Шаг 1. Создание первой виртуальной сети](#step-1-create-the-first-virtual-network)

- [Шаг 2. Создание второй виртуальной сети](#step-2-create-the-second-virtual-network)

- [Шаг 3. Настройте пиринг из первой виртуальной сети для второй виртуальной сети](#step-3-configure-peering-from-the-first-virtual-network-to-the-second-virtual-network)

- [Шаг 4. Настройте пиринг от второй виртуальной сети к первой виртуальной сети](#step-4-configure-peering-from-the-second-virtual-network-to-the-first-virtual-network)


>[!IMPORTANT]
>Не забудьте обновить свойства для вашей среды.

## <a name="step-1-create-the-first-virtual-network"></a>Шаг 1. Создание первой виртуальной сети

На этом шаге вы использование Windows PowerShell поиска логической сети поставщика HNV для создания первой виртуальной сети с одной подсетью. Следующий пример скрипта создает виртуальную сеть Contoso с одной подсетью.

``` PowerShell
#Find the HNV Provider Logical Network  

$logicalnetworks = Get-NetworkControllerLogicalNetwork -ConnectionUri $uri  
foreach ($ln in $logicalnetworks) {  
   if ($ln.Properties.NetworkVirtualizationEnabled -eq "True") {  
      $HNVProviderLogicalNetwork = $ln  
   }  
}   

#Create the Virtual Subnet  

$vsubnet = new-object Microsoft.Windows.NetworkController.VirtualSubnet  
$vsubnet.ResourceId = "Contoso"  
$vsubnet.Properties = new-object Microsoft.Windows.NetworkController.VirtualSubnetProperties  
$vsubnet.Properties.AddressPrefix = "24.30.1.0/24"
$uri=”https://restserver”  

#Create the Virtual Network  

$vnetproperties = new-object Microsoft.Windows.NetworkController.VirtualNetworkProperties  
$vnetproperties.AddressSpace = new-object Microsoft.Windows.NetworkController.AddressSpace  
$vnetproperties.AddressSpace.AddressPrefixes = @("24.30.1.0/24")  
$vnetproperties.LogicalNetwork = $HNVProviderLogicalNetwork  
$vnetproperties.Subnets = @($vsubnet)  
New-NetworkControllerVirtualNetwork -ResourceId "Contoso_VNet1" -ConnectionUri $uri -Properties $vnetproperties
```

## <a name="step-2-create-the-second-virtual-network"></a>Шаг 2. Создание второй виртуальной сети

На этом шаге вы создадите второй виртуальной сети с одной подсетью. Следующий пример скрипта создает виртуальную сеть Woodgrove с одной подсетью.

``` PowerShell

#Create the Virtual Subnet  

$vsubnet = new-object Microsoft.Windows.NetworkController.VirtualSubnet  
$vsubnet.ResourceId = "Woodgrove"  
$vsubnet.Properties = new-object Microsoft.Windows.NetworkController.VirtualSubnetProperties  
$vsubnet.Properties.AddressPrefix = "24.30.2.0/24"  
$uri=”https://restserver”

#Create the Virtual Network  

$vnetproperties = new-object Microsoft.Windows.NetworkController.VirtualNetworkProperties  
$vnetproperties.AddressSpace = new-object Microsoft.Windows.NetworkController.AddressSpace  
$vnetproperties.AddressSpace.AddressPrefixes = @("24.30.2.0/24")  
$vnetproperties.LogicalNetwork = $HNVProviderLogicalNetwork  
$vnetproperties.Subnets = @($vsubnet)  
New-NetworkControllerVirtualNetwork -ResourceId "Woodgrove_VNet1" -ConnectionUri $uri -Properties $vnetproperties
```

## <a name="step-3-configure-peering-from-the-first-virtual-network-to-the-second-virtual-network"></a>Шаг 3. Настройте пиринг из первой виртуальной сети для второй виртуальной сети

На этом шаге необходимо настроить пиринг между первой виртуальной сети и второй виртуальной сети, созданной в предыдущие два шага. В нижеприведенном примере сценария устанавливает пиринг виртуальных сетей из **Contoso_vnet1** для **Woodgrove_vnet1**.

```PowerShell
$peeringProperties = New-Object Microsoft.Windows.NetworkController.VirtualNetworkPeeringProperties
$vnet2 = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "Woodgrove_VNet1"
$peeringProperties.remoteVirtualNetwork = $vnet2

#Indicate whether communication between the two virtual networks
$peeringProperties.allowVirtualnetworkAccess = $true

#Indicates whether forwarded traffic is allowed across the vnets
$peeringProperties.allowForwardedTraffic = $true

#Indicates whether the peer virtual network can access this virtual networks gateway
$peeringProperties.allowGatewayTransit = $false

#Indicates whether this virtual network uses peer virtual networks gateway
$peeringProperties.useRemoteGateways =$false

New-NetworkControllerVirtualNetworkPeering -ConnectionUri $uri -VirtualNetworkId “Contoso_vnet1” -ResourceId “ContosotoWoodgrove” -Properties $peeringProperties

```

>[!IMPORTANT]
>После создания этого пиринга, то виртуальная сеть отображается состояние **инициировано**.

## <a name="step-4-configure-peering-from-the-second-virtual-network-to-the-first-virtual-network"></a>Шаг 4. Настройте пиринг от второй виртуальной сети к первой виртуальной сети

На этом шаге необходимо настроить пиринг между второй виртуальной сети и первой виртуальной сети, созданной на шаге 1 и 2 выше. В нижеприведенном примере сценария устанавливает пиринг виртуальных сетей из **Woodgrove_vnet1** для **Contoso_vnet1**.

```PowerShell
$peeringProperties = New-Object Microsoft.Windows.NetworkController.VirtualNetworkPeeringProperties 
$vnet2=Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "Contoso_VNet1"
$peeringProperties.remoteVirtualNetwork = $vnet2 

# Indicates whether communication between the two virtual networks is allowed 
$peeringProperties.allowVirtualnetworkAccess = $true 

# Indicates whether forwarded traffic will be allowed across the vnets
$peeringProperties.allowForwardedTraffic = $true 

# Indicates whether the peer virtual network can access this virtual network’s gateway
$peeringProperties.allowGatewayTransit = $false 

# Indicates whether this virtual network will use peer virtual network’s gateway
$peeringProperties.useRemoteGateways =$false 

New-NetworkControllerVirtualNetworkPeering -ConnectionUri $uri -VirtualNetworkId “Woodgrove_vnet1” -ResourceId “WoodgrovetoContoso” -Properties $peeringProperties 

```

После создания этого пиринга виртуальной сети, пиринг состояния отображается **подключено** для обоих одноранговых узлов. Теперь виртуальные машины в одной виртуальной сети могут взаимодействовать с виртуальными машинами в пиринговой виртуальной сети.

---