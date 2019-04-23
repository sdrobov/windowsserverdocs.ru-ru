---
title: Создание, удаление или обновление виртуальной сети клиента
description: В этом разделе вы научитесь создавать, удалять и обновлять сетей виртуальный виртуализации сети Hyper-V, после развертывания программно определяемой сети (SDN). Виртуализация сети Hyper-V помогает изолировать сети клиента, таким образом, чтобы сети каждого клиента отдельную сущность. Каждая сущность имеет возможность кросс подключения, не настроив рабочих нагрузок общего доступа.
manager: dougkim
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
ms.date: 08/24/2018
ms.openlocfilehash: a125ec220b4769a57a6be30f1425283afb7f0fe6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59838355"
---
# <a name="create-delete-or-update-tenant-virtual-networks"></a>Создание, удаление или обновление виртуальных сетей клиентов

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе вы научитесь создавать, удалять и обновлять сетей виртуальный виртуализации сети Hyper-V, после развертывания программно определяемой сети (SDN). Виртуализация сети Hyper-V помогает изолировать сети клиента, таким образом, чтобы сети каждого клиента отдельную сущность. Каждая сущность имеет возможность кросс подключения, не настроив рабочих нагрузок общего доступа.   
  
## <a name="create-a-new-virtual-network"></a>Создание новой виртуальной сети  
Создание виртуальной сети для клиента помещает его в определенный домен маршрутизации на узле Hyper-V. Под каждой виртуальной сети есть по крайней мере одной виртуальной подсети. Виртуальные подсети получить определенные с префиксом IP-адрес и ссылаться на ранее определенный ACL.  

Ниже приведены действия, чтобы создать новую виртуальную сеть.

1. Определение префиксов IP-адресов, из которых вы хотите создать виртуальные подсети.   
2. Определение сети логических поставщика, на котором туннелируется трафика клиентов.   
3. Создайте по крайней мере одной виртуальной подсети для каждого префикса IP-адрес, определенный на шаге 1. 
4. (Необязательно) Добавьте ранее созданный списки управления доступом к виртуальные подсети или подключения шлюза для клиентов. 

В следующей таблице содержатся пример идентификатора подсети и префиксы для двух вымышленных клиентов. У клиента Fabrikam есть две виртуальных подсети клиента Contoso имеет три виртуальные подсети.  
 
  
Имя клиента  |ИД виртуальной подсети  |Префикс виртуальной подсети    
---------|---------|---------  
Fabrikam    |5001         |24.30.1.0/24           
Fabrikam     |5002         | 24.30.2.0/20          
Contoso    |6001         |  24.30.1.0/24         
Contoso    | 6002        |  24.30.2.0/24         
Contoso     | 6003        | 24.30.3.0/24          
  
В нижеприведенном примере сценария используются команды Windows PowerShell, экспортированные из **NetworkController** модуль для создания виртуальной сети компании Contoso и одной подсети:   
  
```Powershell  
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
Windows PowerShell можно использовать для обновления существующей подсетью виртуальной или сети.   
  
При запуске в нижеприведенном примере сценария, обновленные ресурсы просто ПОМЕЩАЮТСЯ на сетевой контроллер с тем же идентификатором ресурса. Если ваш клиент Contoso хочет добавить новую подсеть виртуальной (24.30.2.0/24) виртуальную сеть, вам или администратору Contoso можно использовать следующий сценарий.  
  
```PowerShell  
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
  
Чтобы удалить виртуальную сеть можно использовать Windows PowerShell.  
  
В следующем примере Windows PowerShell удаляет клиента виртуальной сети, выполнив HTTP delete к URI идентификатором ресурса.  

```PowerShell  
Remove-NetworkControllerVirtualNetwork -ResourceId "Contoso_Vnet1" -ConnectionUri $uri  
```

