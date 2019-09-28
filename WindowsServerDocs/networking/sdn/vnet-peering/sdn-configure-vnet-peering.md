---
title: Настройка пиринга виртуальной сети
description: Настройка пиринга виртуальных сетей предполагает создание двух виртуальных сетей, которые получают пиринг.
manager: dougkim
ms.prod: windows-server
ms.technology: networking-hv-switch
ms.topic: get-started-article
ms.assetid: ''
ms.author: pashort
author: shortpatti
ms.date: 08/08/2018
ms.openlocfilehash: 4d35501b8d876f2a178a4744d495125dea8da6c7
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405814"
---
# <a name="configure-virtual-network-peering"></a>Настройка пиринга виртуальной сети

>Относится к: Windows Server

В этой процедуре Windows PowerShell используется для создания двух виртуальных сетей, каждая из которых имеет одну подсеть. Затем настройте пиринг между двумя виртуальными сетями, чтобы обеспечить подключение между ними.

- [Шаг 1. Создание первой виртуальной сети](#step-1-create-the-first-virtual-network)

- [Шаг 2. Создание второй виртуальной сети](#step-2-create-the-second-virtual-network)

- [Шаг 3. Настройка пиринга из первой виртуальной сети во вторую](#step-3-configure-peering-from-the-first-virtual-network-to-the-second-virtual-network)

- [Шаг 4. Настройка пиринга из второй виртуальной сети в первую](#step-4-configure-peering-from-the-second-virtual-network-to-the-first-virtual-network)


>[!IMPORTANT]
>Не забудьте обновить свойства среды.

## <a name="step-1-create-the-first-virtual-network"></a>Шаг 1. Создание первой виртуальной сети

На этом шаге вы используете Windows PowerShell для поиска логической сети поставщика HNV, чтобы создать первую виртуальную сеть с одной подсетью. В следующем примере скрипта создается виртуальная сеть Contoso с одной подсетью.

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

На этом шаге вы создадите вторую виртуальную сеть с одной подсетью. В следующем примере скрипта создается виртуальная сеть Woodgrove с одной подсетью.

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

## <a name="step-3-configure-peering-from-the-first-virtual-network-to-the-second-virtual-network"></a>Шаг 3. Настройка пиринга из первой виртуальной сети во вторую

На этом шаге вы настроите пиринг между первой виртуальной сетью и второй виртуальной сетью, созданными в предыдущих двух шагах. В следующем примере сценария устанавливается пиринг виртуальной сети из **Contoso_vnet1** в **Woodgrove_vnet1**.

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
>После создания этого пиринга состояние виртуальной сети будет отображаться как " **инициировано**".

## <a name="step-4-configure-peering-from-the-second-virtual-network-to-the-first-virtual-network"></a>Шаг 4. Настройка пиринга из второй виртуальной сети в первую

На этом шаге вы настроите пиринг между второй виртуальной сетью и первой виртуальной сетью, созданной в шагах 1 и 2 выше. В следующем примере сценария устанавливается пиринг виртуальной сети из **Woodgrove_vnet1** в **Contoso_vnet1**.

```PowerShell
$peeringProperties = New-Object Microsoft.Windows.NetworkController.VirtualNetworkPeeringProperties 
$vnet2=Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "Contoso_VNet1"
$peeringProperties.remoteVirtualNetwork = $vnet2 

# Indicates whether communication between the two virtual networks is allowed 
$peeringProperties.allowVirtualnetworkAccess = $true 

# Indicates whether forwarded traffic will be allowed across the vnets
$peeringProperties.allowForwardedTraffic = $true 

# Indicates whether the peer virtual network can access this virtual network's gateway
$peeringProperties.allowGatewayTransit = $false 

# Indicates whether this virtual network will use peer virtual network's gateway
$peeringProperties.useRemoteGateways =$false 

New-NetworkControllerVirtualNetworkPeering -ConnectionUri $uri -VirtualNetworkId “Woodgrove_vnet1” -ResourceId “WoodgrovetoContoso” -Properties $peeringProperties 

```

После создания этого пиринга состояние пиринга виртуальной сети будет отображаться как " **подключено** " для равноправных узлов. Теперь виртуальные машины в одной виртуальной сети могут взаимодействовать с виртуальными машинами в одноранговой виртуальной сети.

---