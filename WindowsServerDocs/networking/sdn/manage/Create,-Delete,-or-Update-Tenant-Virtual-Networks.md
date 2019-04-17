---
title: Создание, удаление или обновление виртуальных сетей клиентов
description: Этот раздел является частью программного обеспечения определены сетевые руководство о том, как управление рабочими нагрузками клиента и виртуальные сети в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a820826-e829-4ef2-9a20-f74235f8c25b
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 6ef30dcc31593e15c36f846cf6d64afcd4b85f19
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="create-delete-or-update-tenant-virtual-networks"></a>Создание, удаление или обновление виртуальных сетей клиентов

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать, чтобы узнать, как создание, удаление и обновление виртуальных сетей Hyper-V сети виртуализации после развертывания программного обеспечения определяемая сеть (SDN).  
  
С помощью виртуализации сети Hyper-V, можно изолировать сетями, чтобы сети каждого клиента — это объект, полностью отделенного без возможности подключения между, если не задан рабочих нагрузок общего доступа.  
  
Можно создать новые виртуальные сети для клиентов, можно изменять существующие виртуальные сети и если клиент больше не нужна определенным ресурсам или клиента больше не является вашим клиентом, можно удалить клиента виртуальных сетей.  
  
## <a name="create-a-new-virtual-network"></a>Создать новую виртуальную сеть  
  
При создании виртуальной сети для клиента будет располагаться в пределах уникальный домену маршрутизации на узле Hyper-V.  
  
Ниже приведены действия, чтобы создать новую виртуальную сеть.  
  
1. Определите префиксы IP-адресов, с которых вы хотите создать виртуальные подсети.   
2. Определите сеть логических поставщика, на котором туннель используется для трафика клиентов.   
3. Создайте по крайней мере одной виртуальной подсети для каждого IP префикса, определенного на шаге 1.   
  
>[!NOTE]  
>Под каждой виртуальной сети нет по крайней мере одной виртуальной подсети. Виртуальные подсети определяются IP, префикса и ссылаться на ранее определенный список управления доступом.  
  
При необходимости после выполнения этих действий, можно также добавить списки управления доступом, ранее созданного для виртуальных подсетей, или добавить подключения через шлюз для клиентов.    
  
В следующей таблице представлены пример идентификатора подсети и префиксы для двух вымышленные клиентов. Клиент Fabrikam имеет два виртуальных подсетей, пока клиенте Contoso содержит три виртуальные подсети.  
  
  
  
Имя клиента  |Идентификатор виртуальной подсети  |Префикс виртуальные подсети    
---------|---------|---------  
Fabrikam    |5001         |24.30.1.0/24           
Fabrikam     |5002         | 24.30.2.0/20          
Contoso    |6001         |  24.30.1.0/24         
Contoso    | 6002        |  24.30.2.0/24         
Contoso     | 6003        | 24.30.3.0/24          
  
В следующем примере сценария используется команд Windows PowerShell, экспортированные из **NetworkController** модуль для создания виртуальной сети и подсети Contoso:   
  
```  
import-module networkcontroller  
$URI = "https://ncrest.contoso.local"  
  
#Find the HNV Provider Logical Network  
  
$logicalnetworks = Get-NetworkControllerLogicalNetwork -ConnectionUri $uri  
foreach ($ln in $logicalnetworks) {  
   if ($ln.Properties.NetworkVirtualizationEnabled -eq "True") {  
      $HNVProviderLogicalNetwork = $ln  
   }  
}   
  
#Find the Access Control List to user per virtual subnet  
  
$acllist = Get-NetworkControllerAccessControlList -ConnectionUri $uri -ResourceId "AllowAll"  
  
#Create the Virtual Subnet  
  
$vsubnet = new-object Microsoft.Windows.NetworkController.VirtualSubnet  
$vsubnet.ResourceId = "Contoso_WebTier"  
$vsubnet.Properties = new-object Microsoft.Windows.NetworkController.VirtualSubnetProperties  
$vsubnet.Properties.AccessControlList = $acllist  
$vsubnet.Properties.AddressPrefix = "24.30.1.0/24"  
  
#Create the Virtual Network  
  
$vnetproperties = new-object Microsoft.Windows.NetworkController.VirtualNetworkProperties  
$vnetproperties.AddressSpace = new-object Microsoft.Windows.NetworkController.AddressSpace  
$vnetproperties.AddressSpace.AddressPrefixes = @("24.30.1.0/24")  
$vnetproperties.LogicalNetwork = $HNVProviderLogicalNetwork  
$vnetproperties.Subnets = @($vsubnet)  
New-NetworkControllerVirtualNetwork -ResourceId "Contoso_VNet1" -ConnectionUri $uri -Properties $vnetproperties  
  
  
```  
  
## <a name="modify-an-existing-virtual-network"></a>Изменение существующей виртуальной сети  
Windows PowerShell можно использовать для обновления существующей виртуальной подсети или сети.   
  
При запуске в следующем примере сценария обновленные ресурсы ПОМЕЩАЮТСЯ просто для сетевого контроллера с тем же идентификатором ресурса. Если в клиенте Contoso хочет добавить новый виртуальной подсети (24.30.2.0/24) к виртуальной сети, вами или администратором Contoso можно использовать следующий сценарий.  
  
```  
$acllist = Get-NetworkControllerAccessControlList -ConnectionUri $uri -ResourceId "AllowAll"  
  
$vnet = Get-NetworkControllerVirtualNetwork -ResourceId "Contoso_VNet1" -ConnectionUri $uri  
  
$vnet.properties.AddressSpace.AddressPrefixes += "24.30.2.0/24"  
  
$vsubnet = new-object Microsoft.Windows.NetworkController.VirtualSubnet  
$vsubnet.ResourceId = "Contoso_DBTier"  
$vsubnet.Properties = new-object Microsoft.Windows.NetworkController.VirtualSubnetProperties  
$vsubnet.Properties.AccessControlList = $acllist  
$vsubnet.Properties.AddressPrefix = "24.30.2.0/24"  
  
$vnet.properties.Subnets += $vsubnet  
  
New-NetworkControllerVirtualNetwork -ResourceId "Contoso_VNet1" -ConnectionUri $uri -properties $vnet.properties  
  
```  
  
## <a name="delete-a-virtual-network"></a>Удаление виртуальной сети  
  
Чтобы удалить виртуальную сеть, можно использовать Windows PowerShell.  
  
Следующий пример Windows PowerShell удаляет клиента виртуальной сети, выдавая HTTP delete URI ресурса кода.  
  
    Remove-NetworkControllerVirtualNetwork -ResourceId "Contoso_Vnet1" -ConnectionUri $uri  


