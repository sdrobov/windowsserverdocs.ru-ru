---
title: Используйте доступ списки управления (доступом ACL) для управления потоком сетевого трафика центра обработки данных
description: В этом разделе вы узнаете, как настроить списки управления доступом (ACL) для управления поток трафика данных при использовании брандмауэра центра обработки данных и списки управления доступом в виртуальных подсетях. Включите и настройте брандмауэр центра обработки данных, создав списки управления доступом, которые применяются к виртуальной подсети или сетевому интерфейсу.
manager: dougkim
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a7ac5af-85e9-4440-a631-6a3a38e9015d
ms.author: pashort
author: shortpatti
ms.date: 08/27/2018
ms.openlocfilehash: 1364261f7ab1e732ac77b7c90d49c245aa8cbc25
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59861425"
---
# <a name="use-access-control-lists-acls-to-manage-datacenter-network-traffic-flow"></a>Используйте доступ списки управления (доступом ACL) для управления потоком сетевого трафика центра обработки данных

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе вы узнаете, как настроить списки управления доступом (ACL) для управления поток трафика данных при использовании брандмауэра центра обработки данных и списки управления доступом в виртуальных подсетях. Включите и настройте брандмауэр центра обработки данных, создав списки управления доступом, которые применяются к виртуальной подсети или сетевому интерфейсу.   
  
Следующие примеры в этом разделе показано, как использовать Windows PowerShell для создания этих списков управления доступом.  
  
## <a name="configure-datacenter-firewall-to-allow-all-traffic"></a>Настройте брандмауэр центра обработки данных, чтобы разрешить передачу всего трафика  
  
После развертывания SDN, для сети следует проверить в новой среде.  Для этого необходимо создайте правило для брандмауэра центра обработки данных, позволяющий весь сетевой трафик, без ограничений.   
  
Записи в следующей таблице можно используйте для создания набора правила, разрешающие весь входящий и исходящий сетевой трафик.
  
|Исходный IP-адрес|IP-адрес назначения|Используемый протокол|Порт источника|Порт назначения|Direction|Действие|Priority |   
|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|
|*    |   *      |   Все      |    *     |      *   |     Входящий    |   Разрешить      |   100  |      
|*    |     *    |     Все    |     *    |     *    |   Исходящий      |  Разрешить       |  110  |
---       
  
### <a name="example-create-an-acl"></a>Пример. Создание ACL 
В этом примере создается список управления Доступом с два правила:
  
1. **AllowAll_Inbound** -разрешает весь сетевой трафик, передаваемый в сетевой интерфейс, где настроен этот ACL.    
2. **AllowAllOutbound** -разрешает весь трафик, передаваемый из сетевого интерфейса. Этот список управления Доступом, определяемого идентификатором ресурса «AllowAll-1» теперь готов для использования в виртуальных подсетей и сетевых интерфейсов.  
  
В нижеприведенном примере сценария используются команды Windows PowerShell, экспортированные из **NetworkController** модуль создания этого списка ACL.  
  
  
```PowerShell
$ruleproperties = new-object Microsoft.Windows.NetworkController.AclRuleProperties  
$ruleproperties.Protocol = "All"  
$ruleproperties.SourcePortRange = "0-65535"  
$ruleproperties.DestinationPortRange = "0-65535"  
$ruleproperties.Action = "Allow"  
$ruleproperties.SourceAddressPrefix = "*"  
$ruleproperties.DestinationAddressPrefix = "*"  
$ruleproperties.Priority = "100"  
$ruleproperties.Type = "Inbound"  
$ruleproperties.Logging = "Enabled"  
$aclrule1 = new-object Microsoft.Windows.NetworkController.AclRule  
$aclrule1.Properties = $ruleproperties  
$aclrule1.ResourceId = "AllowAll_Inbound"  
$ruleproperties = new-object Microsoft.Windows.NetworkController.AclRuleProperties  
$ruleproperties.Protocol = "All"  
$ruleproperties.SourcePortRange = "0-65535"  
$ruleproperties.DestinationPortRange = "0-65535"  
$ruleproperties.Action = "Allow"  
$ruleproperties.SourceAddressPrefix = "*"  
$ruleproperties.DestinationAddressPrefix = "*"  
$ruleproperties.Priority = "110"  
$ruleproperties.Type = "Outbound"  
$ruleproperties.Logging = "Enabled"  
$aclrule2 = new-object Microsoft.Windows.NetworkController.AclRule  
$aclrule2.Properties = $ruleproperties  
$aclrule2.ResourceId = "AllowAll_Outbound"  
$acllistproperties = new-object Microsoft.Windows.NetworkController.AccessControlListProperties  
$acllistproperties.AclRules = @($aclrule1, $aclrule2)  
New-NetworkControllerAccessControlList -ResourceId "AllowAll" -Properties $acllistproperties -ConnectionUri <NC REST FQDN>  
```  
  
>[!NOTE]  
>Справочник по командам Windows PowerShell для сетевого контроллера находится в разделе [командлеты сетевого контроллера](https://technet.microsoft.com/library/mt576401.aspx).  
  
## <a name="use-acls-to-limit-traffic-on-a-subnet"></a>Используйте списки управления доступом, чтобы ограничить трафик в подсети  
В этом примере создайте ACL, который запрещает обмен данными между собой виртуальных машин в подсети, 192.168.0.0/24. Этот тип ACL полезно для ограничения возможности злоумышленника для распределения режиме бокового смещения в пределах подсети, по-прежнему предоставляя виртуальные машины для получения запросов из вне подсети, а также для взаимодействия с другими службами в других подсетях.   
  
  
|Исходный IP-адрес|IP-адрес назначения|Используемый протокол|Порт источника|Порт назначения|Direction|Действие|Priority |  
|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|  
|192.168.0.1    | * | Все | * | * | Входящий|   Разрешить      |   100        |
|* |192.168.0.1 | Все | * | * | Исходящий|  Разрешить       |  101         |
|192.168.0.0/24 | * | Все | * | * | Входящий| Блокирование | 102  |
|* | 192.168.0.0/24 |Все| * | * | Исходящий | Блокирование |103  |
|* | *  |Все| * | * | Входящий | Разрешить |104  |
|* | *  |Все| * | * | Исходящий | Разрешить |105  |
--- 

Список ACL, созданный с помощью пример сценария ниже, с идентификатором ресурса **подсети-192-168-0-0**, теперь можно применять к подсети виртуальной сети, которая использует адрес подсети «192.168.0.0/24».  Любого сетевого интерфейса, подключенных к подсети виртуальной сети, автоматически получает выше правила ACL применяется.  
  
Ниже приведен пример сценария с помощью команды Windows Powershell для создания этого списка ACL с помощью REST API сетевого контроллера.  
  
```PowerShell  
import-module networkcontroller  
$ncURI = "https://mync.contoso.local"  
$aclrules = @()  
  
$ruleproperties = new-object Microsoft.Windows.NetworkController.AclRuleProperties  
$ruleproperties.Protocol = "All"  
$ruleproperties.SourcePortRange = "0-65535"  
$ruleproperties.DestinationPortRange = "0-65535"  
$ruleproperties.Action = "Allow"  
$ruleproperties.SourceAddressPrefix = "192.168.0.1"  
$ruleproperties.DestinationAddressPrefix = "*"  
$ruleproperties.Priority = "100"  
$ruleproperties.Type = "Inbound"  
$ruleproperties.Logging = "Enabled"  
  
$aclrule = new-object Microsoft.Windows.NetworkController.AclRule  
$aclrule.Properties = $ruleproperties  
$aclrule.ResourceId = "AllowRouter_Inbound"  
$aclrules += $aclrule  
  
$ruleproperties = new-object Microsoft.Windows.NetworkController.AclRuleProperties  
$ruleproperties.Protocol = "All"  
$ruleproperties.SourcePortRange = "0-65535"  
$ruleproperties.DestinationPortRange = "0-65535"  
$ruleproperties.Action = "Allow"  
$ruleproperties.SourceAddressPrefix = "*"  
$ruleproperties.DestinationAddressPrefix = "192.168.0.1"  
$ruleproperties.Priority = "101"  
$ruleproperties.Type = "Outbound"  
$ruleproperties.Logging = "Enabled"  
  
$aclrule = new-object Microsoft.Windows.NetworkController.AclRule  
$aclrule.Properties = $ruleproperties  
$aclrule.ResourceId = "AllowRouter_Outbound"  
$aclrules += $aclrule  
  
$ruleproperties = new-object Microsoft.Windows.NetworkController.AclRuleProperties  
$ruleproperties.Protocol = "All"  
$ruleproperties.SourcePortRange = "0-65535"  
$ruleproperties.DestinationPortRange = "0-65535"  
$ruleproperties.Action = "Deny"  
$ruleproperties.SourceAddressPrefix = "192.168.0.0/24"  
$ruleproperties.DestinationAddressPrefix = "*"  
$ruleproperties.Priority = "102"  
$ruleproperties.Type = "Inbound"  
$ruleproperties.Logging = "Enabled"  
  
$aclrule = new-object Microsoft.Windows.NetworkController.AclRule  
$aclrule.Properties = $ruleproperties  
$aclrule.ResourceId = "DenySubnet_Inbound"  
$aclrules += $aclrule  
  
$ruleproperties = new-object Microsoft.Windows.NetworkController.AclRuleProperties  
$ruleproperties.Protocol = "All"  
$ruleproperties.SourcePortRange = "0-65535"  
$ruleproperties.DestinationPortRange = "0-65535"  
$ruleproperties.Action = "Deny"  
$ruleproperties.SourceAddressPrefix = "*"  
$ruleproperties.DestinationAddressPrefix = "192.168.0.0/24"  
$ruleproperties.Priority = "103"  
$ruleproperties.Type = "Outbound"  
$ruleproperties.Logging = "Enabled"  
  
$aclrule = new-object Microsoft.Windows.NetworkController.AclRule  
$aclrule.Properties = $ruleproperties  
$aclrule.ResourceId = "DenySubnet_Outbound"  
  
$ruleproperties = new-object Microsoft.Windows.NetworkController.AclRuleProperties  
$ruleproperties.Protocol = "All"  
$ruleproperties.SourcePortRange = "0-65535"  
$ruleproperties.DestinationPortRange = "0-65535"  
$ruleproperties.Action = "Allow"  
$ruleproperties.SourceAddressPrefix = "*"  
$ruleproperties.DestinationAddressPrefix = "*"  
$ruleproperties.Priority = "104"  
$ruleproperties.Type = "Inbound"  
$ruleproperties.Logging = "Enabled"  
  
$aclrule = new-object Microsoft.Windows.NetworkController.AclRule  
$aclrule.Properties = $ruleproperties  
$aclrule.ResourceId = "AllowAll_Inbound"  
$aclrules += $aclrule  
  
$ruleproperties = new-object Microsoft.Windows.NetworkController.AclRuleProperties  
$ruleproperties.Protocol = "All"  
$ruleproperties.SourcePortRange = "0-65535"  
$ruleproperties.DestinationPortRange = "0-65535"  
$ruleproperties.Action = "Allow"  
$ruleproperties.SourceAddressPrefix = "*"  
$ruleproperties.DestinationAddressPrefix = "*"  
$ruleproperties.Priority = "105"  
$ruleproperties.Type = "Outbound"  
$ruleproperties.Logging = "Enabled"  
  
$aclrule = new-object Microsoft.Windows.NetworkController.AclRule  
$aclrule.Properties = $ruleproperties  
$aclrule.ResourceId = "AllowAll_Outbound"  
$aclrules += $aclrule  
  
$acllistproperties = new-object Microsoft.Windows.NetworkController.AccessControlListProperties  
$acllistproperties.AclRules = $aclrules  
  
New-NetworkControllerAccessControlList -ResourceId "Subnet-192-168-0-0" -Properties $acllistproperties -ConnectionUri $ncURI   
```  
  
