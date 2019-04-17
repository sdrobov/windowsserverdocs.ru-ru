---
title: Используйте списки управления доступом (ACL) для управления потоком центра обработки данных сетевого трафика
description: Этот раздел является частью программного обеспечения определены сетевые руководство о том, как управление рабочими нагрузками клиента и виртуальные сети в Windows Server 2016.
manager: brianlic
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
ms.openlocfilehash: 64b7e1abf1ddb8132a8c6692fe82521c589f32df
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="use-access-control-lists-acls-to-manage-datacenter-network-traffic-flow"></a>Используйте списки управления доступом (ACL) для управления потоком центра обработки данных сетевого трафика

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать, чтобы узнать, как настроить списки управления доступом, управление потоком трафика данных, используя брандмауэр центра обработки данных и списки управления доступом в виртуальных подсетях.  
  
Можно включить и настроить брандмауэр центра обработки данных путем создания ACL, которые применяются к виртуальной подсети или сетевого интерфейса.  
  
В следующих примерах использования Windows PowerShell для создания эти списки управления доступом.  
  
## <a name="configure-datacenter-firewall-to-allow-all-traffic"></a>Настройте брандмауэр центра обработки данных, чтобы разрешить весь трафик  
  
После развертывания SDN, рекомендуется Проверьте подключение базовой сети в новой среде.  
  
Чтобы выполнить это, можно создать правило для брандмауэра центра обработки данных, который позволяет весь сетевой трафик, без ограничений.   
  
Чтобы создать набор правил, разрешающих весь входящий и исходящий сетевой трафик, можно использовать записи в таблице ниже.  
  
  
  
Исходный IP-адрес|Конечный IP|Протокол|Порт источника|Порт назначения|Направление|Действие|Приоритет   
---------|---------|---------|---------|---------|---------|---------|---------  
*    |   *      |   Все      |    *     |      *   |     Входящих подключений    |   Разрешить      |   100        
*    |     *    |     Все    |     *    |     *    |   Исходящих подключений      |  Разрешить       |  110         
  
  
В этом примере сценария создает ACL, который содержит два правила:    
- Первое правило «AllowAll_Inbound» позволяет весь сетевой трафик для передачи в сетевой интерфейс, где был установлен этот ACL.    
- Второе правило «AllowAllOutbound» позволяет весь трафик, передаваемый из сетевого интерфейса.  
Этот ACL с идентификатором ресурса «AllowAll-1» теперь готовы к использованию в виртуальных подсетях и сетевых интерфейсов.  
  
В следующем примере сценария используется команд Windows PowerShell, экспортированные из **NetworkController** модуль создания этот ACL.  
  
  
```  
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
  
## <a name="use-acls-to-limit-traffic-on-a-subnet"></a>Используйте списки управления доступом, чтобы ограничить объем трафика для подсети  
  
В этом примере можно использовать для создания ACL, который предотвращает виртуальных машин (ВМ) в подсети 192.168.0.0/24 взаимодействовать друг с другом.   
  
Этот тип ACL полезно для ограничения возможности злоумышленник сторону распространения в пределах подсети, оставляя виртуальные машины для получения запросов от вне подсети, а также взаимодействовать с другими службами в других подсетях.  
  
  
Исходный IP-адрес|Конечный IP|Протокол|Порт источника|Порт назначения|Направление|Действие|Приоритет   
---------|---------|---------|---------|---------|---------|---------|---------  
192.168.0.1    | * | Все | * | * | Входящих подключений|   Разрешить      |   100        
* |192.168.0.1 | Все | * | * | Исходящих подключений|  Разрешить       |  101         
192.168.0.0/24 | * | Все | * | * | Входящих подключений| Блок | 102  
* | 192.168.0.0/24 |Все| * | * | Исходящих подключений | Блок |103  
* | *  |Все| * | * | Входящих подключений | Разрешить |104  
* | *  |Все| * | * | Исходящих подключений | Разрешить |105  
  
ACL созданные ниже, пример сценария с идентификатором ресурса **подсети-192-168-0-0**, теперь может быть применен к подсети виртуальной сети, которая использует адрес подсети «192.168.0.0/24».  Любой сетевого интерфейса, подключенного к подсети виртуальной сети, автоматически получает выше правила списков ACL применяется.  
  
Ниже приведен пример сценария с помощью команды Windows Powershell для создания этого списка ACL с помощью API-Интерфейс REST сетевого контроллера:  
  
```  
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
  
