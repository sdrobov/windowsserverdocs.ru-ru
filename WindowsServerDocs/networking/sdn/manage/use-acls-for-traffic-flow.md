---
title: Использование списков управления доступом (ACL) для управления потоком сетевого трафика центра обработки данных
description: В этом разделе вы узнаете, как настроить списки управления доступом (ACL) для управления потоком трафика данных с помощью брандмауэра и списков ACL в виртуальных подсетях. Брандмауэр центра обработки данных включается и настраивается путем создания списков управления доступом, которые применяются к виртуальной подсети или сетевому интерфейсу.
manager: dougkim
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a7ac5af-85e9-4440-a631-6a3a38e9015d
ms.author: lizross
author: eross-msft
ms.date: 08/27/2018
ms.openlocfilehash: 1f18ad9ddb0ea1a7575f6fcb26189f36f818ada2
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80317485"
---
# <a name="use-access-control-lists-acls-to-manage-datacenter-network-traffic-flow"></a>Использование списков управления доступом (ACL) для управления потоком сетевого трафика центра обработки данных

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе вы узнаете, как настроить списки управления доступом (ACL) для управления потоком трафика данных с помощью брандмауэра и списков ACL в виртуальных подсетях. Брандмауэр центра обработки данных включается и настраивается путем создания списков управления доступом, которые применяются к виртуальной подсети или сетевому интерфейсу.   

В следующих примерах в этом разделе показано, как использовать Windows PowerShell для создания этих списков ACL.  

## <a name="configure-datacenter-firewall-to-allow-all-traffic"></a>Настройка брандмауэра центра обработки данных для разрешения всего трафика  

После развертывания SDN необходимо протестировать базовое сетевое подключение в новой среде.  Чтобы сделать это, создайте правило для брандмауэра центра обработки данных, которое разрешает весь сетевой трафик без ограничений.   

Используйте записи в следующей таблице для создания набора правил, разрешающих весь входящий и исходящий сетевой трафик.


| Исходный IP-адрес | IP-адрес назначения | Протокол | Порт источника | Порт назначения | Направление | Действие | Priority |
|:---------:|:--------------:|:--------:|:-----------:|:----------------:|:---------:|:------:|:--------:|
|    \*     |       \*       |   Все    |     \*      |        \*        |  Входящий  | Разрешение  |   100    |
|    \*     |       \*       |   Все    |     \*      |        \*        | Исходящий  | Разрешение  |   110    |

---       

### <a name="example-create-an-acl"></a>Пример. Создание списка управления доступом 
В этом примере вы создадите список ACL с двумя правилами:

1. **AllowAll_Inbound** — разрешает передачу всего сетевого трафика в сетевой интерфейс, где настроен этот список ACL.    
2. **Алловаллаутбаунд** — разрешает передачу всего трафика из сетевого интерфейса. Этот список ACL, определяемый идентификатором ресурса "Алловалл-1", теперь готов к использованию в виртуальных подсетях и сетевых интерфейсах.  

В следующем примере скрипта используются команды Windows PowerShell, экспортированные из модуля **нетворкконтроллер** для создания этого списка ACL.  


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

## <a name="use-acls-to-limit-traffic-on-a-subnet"></a>Использование списков управления доступом для ограничения трафика в подсети  
В этом примере создается список ACL, который предотвращает обмен данными между виртуальными машинами в подсети 192.168.0.0/24. Этот тип ACL полезен для ограничения возможности злоумышленника распределяться позже в подсети, в то же время позволяя виртуальным машинам получать запросы извне подсети, а также взаимодействовать с другими службами в других подсетях.   


|   Исходный IP-адрес    | IP-адрес назначения | Протокол | Порт источника | Порт назначения | Направление | Действие | Priority |
|:--------------:|:--------------:|:--------:|:-----------:|:----------------:|:---------:|:------:|:--------:|
|  адреса   |       \*       |   Все    |     \*      |        \*        |  Входящий  | Разрешение  |   100    |
|       \*       |  адреса   |   Все    |     \*      |        \*        | Исходящий  | Разрешение  |   101    |
| 192.168.0.0/24 |       \*       |   Все    |     \*      |        \*        |  Входящий  | Блокировать  |   102    |
|       \*       | 192.168.0.0/24 |   Все    |     \*      |        \*        | Исходящий  | Блокировать  |   103    |
|       \*       |       \*       |   Все    |     \*      |        \*        |  Входящий  | Разрешение  |   104    |
|       \*       |       \*       |   Все    |     \*      |        \*        | Исходящий  | Разрешение  |   105    |

--- 

Список управления доступом, созданный в приведенном ниже примере сценария, определяемый с помощью идентификатора ресурса **Subnet-192-168-0-0**, теперь можно применить к подсети виртуальной сети, которая использует адрес подсети 192.168.0.0/24.  Любой сетевой интерфейс, подключенный к этой подсети виртуальной сети, автоматически получает примененные выше правила ACL.  

Ниже приведен пример сценария, использующего команды Windows PowerShell для создания списка ACL с помощью сетевого контроллера REST API.  

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

