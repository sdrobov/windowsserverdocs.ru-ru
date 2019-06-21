---
title: Справочник по командам BGP для Windows PowerShell
description: Можно использовать в этом разделе как ссылка, при написании сценариев Windows PowerShell в Windows Server 2016, чтобы добавить, настроить и удалить возможности BGP из маршрутизаторов шлюза удаленного доступа и удаленного доступа к локальной сети (LAN).
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b0240a3-b927-4a1e-b241-5f8f29a9552f
ms.author: pashort
author: shortpatti
ms.openlocfilehash: ef1dc1c8193a2f923f8154164e6b59fe54202527
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67283651"
---
# <a name="bgp-windows-powershell-command-reference"></a>Справочник по командам BGP для Windows PowerShell

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Можно использовать в этом разделе как ссылка, при написании сценариев Windows PowerShell для добавления, настройки и удалить возможности BGP из маршрутизаторов шлюза удаленного доступа и удаленного доступа к локальной сети (LAN).  
  
Эти команды BGP входят в набор для Windows Server 2016 команд Windows PowerShell удаленного доступа. Этот раздел поможет вам быстро найти команды BGP, которые вы хотите использовать в скриптах.  
  
Дополнительные сведения о всех команд удаленного доступа, см. в разделе [командлеты удаленного доступа](https://technet.microsoft.com/library/hh918399.aspx).  
  
## <a name="bgp-command-reference"></a>Справочник по командам BGP  
В следующих разделах имя команды, назначение и синтаксис для каждой команды BGP, а также ссылку на команду в ссылке удаленного доступа, который содержит более подробные сведения о каждой из них.  
  
Этот справочник содержит следующие разделы.  
  
-   [Добавление команд](#bkmk_add)  
  
-   [Очистить команды](#bkmk_clear)  
  
-   [Отключение и Включение команды](#bkmk_disable)  
  
-   [Получить команды](#bkmk_get)  
  
-   [Команды установки](#bkmk_install)  
  
-   [Удалить команды](#bkmk_remove)  
  
-   [Набор команд](#bkmk_set)  
  
-   [Start и Stop команды](#bkmk_start)  
  
-   [Команды удаления](#bkmk_uninstall)  
  
### <a name="bkmk_add"></a>Добавление команд  
Ниже приведены команды Добавить BGP.  
  
[Добавить BgpCustomRoute](https://technet.microsoft.com/library/dn262684.aspx)  
  
Добавляет настраиваемые маршруты в таблицу маршрутизации BGP.  
  
```  
Add-BgpCustomRoute [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-Interface <String[]> ] [-Network <String[]> ] [-PassThru] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Добавление указано](https://technet.microsoft.com/library/dn262687.aspx)  
  
Добавляет новый узел BGP.  
  
```  
Add-BgpPeer [-Name] <String> -LocalIPAddress <IPAddress> -PeerASN <UInt32> -PeerIPAddress <IPAddress> [-CimSession <CimSession[]> ] [-HoldTimeSec <UInt16> ] [-IdleHoldTimeSec <UInt16> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-LocalASN <UInt32> ] [-MaxAllowedPrefix <UInt32> ] [-OperationMode <OperationMode> {Mixed | Server} ] [-PassThru] [-PeeringMode <PeeringMode> {Automatic | Manual} ] [-RouteReflectorClient <Boolean> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Weight <UInt16> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Добавить BgpRouteAggregate](https://technet.microsoft.com/library/mt463113.aspx)  
  
Добавляет новый маршрут агрегатные для определенных маршрутов BGP.  
  
```  
Add-BgpRouteAggregate -Prefix <String> [-AttributePolicy <String[]> ] [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-PassThru] [-PreserveASPath <PreserveASPath> ] [-RoutingDomain <String> ] [-SummaryOnly <SummaryOnly> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Добавить BgpRouter](https://technet.microsoft.com/library/dn262665.aspx)  
  
Добавляет маршрутизатор BGP для указанного идентификатора клиента.  
  
```  
Add-BgpRouter -BgpIdentifier <IPAddress> -LocalASN <UInt32> [-CimSession <CimSession[]> ] [-ClientToClientReflection <ClientToClientReflection> ] [-ClusterId <UInt32> ] [-CompareMEDAcrossASN <Boolean> ] [-DefaultGatewayRouting <Boolean> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-IPv6Routing <IPv6RoutingState> {Disabled | Enabled} ] [-LocalIPv6Address <IPAddress> ] [-PassThru] [-RouteReflector <RouteReflector> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-TransitRouting <TransitRouting> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Добавить BgpRoutingPolicy](https://technet.microsoft.com/library/dn262662.aspx)  
  
Добавляет политику маршрутизации BGP в хранилище политики.  
  
```  
Add-BgpRoutingPolicy [-Name] <String> [-PolicyType] <PolicyType> {Deny | Allow | ModifyAttribute} [-AddCommunity <String[]> ] [-CimSession <CimSession[]> ] [-ClearMED] [-Force] [-IgnorePrefix <String[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-MatchASNRange <UInt32[]> ] [-MatchCommunity <String[]> ] [-MatchNextHop <IPAddress[]> ] [-MatchPrefix <String[]> ] [-NewLocalPref <UInt32]> ] [-NewMED <UInt32]> ] [-NewNextHop <IPAddress> ] [-PassThru] [-RemoveAllCommunities] [-RemoveCommunity <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Добавить BgpRoutingPolicyForPeer](https://technet.microsoft.com/library/dn262680.aspx)  
  
Добавление политики маршрутизации BGP узлов BGP.  
  
```  
Add-BgpRoutingPolicyForPeer -Direction <PolicyDirection> {Ingress | Egress} -PolicyName <String[]> [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-PeerName <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="bkmk_clear"></a>Очистить команды  
Ниже приведены команды, снимите флажок для BGP  
  
[Clear-BgpRouteFlapDampening](https://technet.microsoft.com/library/mt463114.aspx)  
  
Очищает flap маршрута, гашение сведения для указанного набора маршруты BGP.  
  
```  
Clear-BgpRouteFlapDampening [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-Prefix <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="bkmk_disable"></a>Отключение и Включение команды  
Ниже приведены команды отключения и включения для BGP  
  
[Disable-BgpRouteFlapDampening](https://technet.microsoft.com/library/mt463100.aspx)  
  
Отключает маршрут гашение для хлопания маршруты BGP.  
  
```  
Disable-BgpRouteFlapDampening [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Enable-BgpRouteFlapDampening](https://technet.microsoft.com/library/mt463102.aspx)  
  
Маршрут включает гашение для хлопания маршруты BGP.  
  
```  
Enable-BgpRouteFlapDampening [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-PassThru] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="bkmk_get"></a>Получить команды  
Ниже приведены команды Get для BGP.  
  
[Get-BgpCustomRoute](https://technet.microsoft.com/library/dn262664.aspx)  
  
Возвращает сведения о пользовательских маршрутов от маршрутизатора BGP.  
  
```  
Get-BgpCustomRoute [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get указано](https://technet.microsoft.com/library/dn262659.aspx)  
  
Возвращает сведения о конфигурации для узлов BGP.  
  
```  
Get-BgpPeer [[-Name] <String[]> ] [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-BgpRouteAggregate](https://technet.microsoft.com/library/mt463103.aspx)  
  
Получает все агрегированные маршруты BGP, настроенную администратором.  
  
```  
Get-BgpRouteAggregate [-CimSession <CimSession[]> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-Prefix <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-BgpRouteFlapDampening](https://technet.microsoft.com/library/mt463108.aspx)  
  
Возвращает конфигурацию отбрасывания обработчика маршрутов BGP.  
  
```  
Get-BgpRouteFlapDampening [-CimSession <CimSession[]> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-BgpRouteInformation](https://technet.microsoft.com/library/dn262667.aspx)  
  
Извлекает сведения о маршруте BGP для префиксов сети один или несколько из таблицы маршрутизации BGP.  
  
```  
Get-BgpRouteInformation [-CimSession <CimSession[]> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-Network <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Type <RouteType> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-BgpRouter](https://technet.microsoft.com/library/dn262660.aspx)  
  
Возвращает сведения о конфигурации для маршрутизаторов BGP.  
  
```  
Get-BgpRouter [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String[]> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-BgpRoutingPolicy](https://technet.microsoft.com/library/dn262672.aspx)  
  
Возвращает сведения о конфигурации политик маршрутизации BGP.  
  
```  
Get-BgpRoutingPolicy [[-Name] <String[]> ] [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-PolicyType <PolicyType> {Deny | Allow | ModifyAttribute} ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-BgpStatistics](https://technet.microsoft.com/library/dn262685.aspx)  
  
Извлекает BGP пиринг сообщениями и маршрутам объявления статистику.  
  
```  
Get-BgpStatistics [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-PeerName <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="bkmk_install"></a>Команды установки  
Ниже приведены команды установки для шлюза RAS и BGP.  
  
[Install-RemoteAccess](https://technet.microsoft.com/library/hh918408.aspx)  
  
Выполняет проверки предварительных требований для DirectAccess (DA) и убедитесь, что это может быть установлено, устанавливает DA для удаленного доступа (RA) (включает управление удаленным клиентам), или для управления только для удаленных клиентов, устанавливает VPN (удаленного доступа VPN и VPN сеть), и устанавливает маршрутизации BGP.  
  
```  
Parameter Set: MultiTenant  
Install-RemoteAccess [-MultiTenancy] [-CapacityKbps <UInt64> ] [-CimSession <CimSession[]> ] [-ComputerName <String> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-MsgAuthenticator <String> {Enabled | Disabled} ] [-PassThru] [-RadiusPort <UInt16> ] [-RadiusScore <Byte> ] [-RadiusServer <String> ] [-RadiusTimeout <UInt32> ] [-SharedSecret <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
  
Parameter Set: Vpn  
Install-RemoteAccess [-VpnType] <String> {Vpn | VpnS2S | SstpProxy | RoutingOnly} [-CimSession <CimSession[]> ] [-ComputerName <String> ] [-EntrypointName <String> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-IPAddressRange <String[]> ] [-IPv6Prefix <String> ] [-Legacy] [-MsgAuthenticator <String> {Enabled | Disabled} ] [-PassThru] [-RadiusPort <UInt16> ] [-RadiusScore <Byte> ] [-RadiusServer <String> ] [-RadiusTimeout <UInt32> ] [-SharedSecret <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
> [!IMPORTANT]  
> При установке шлюза удаленного доступа в мультитенантном режиме, необходимо указать, включен ли протокол BGP для каждого клиента с помощью **Enable-RemoteAccessRoutingDomain** команду Windows PowerShell с **-тип** значение параметра **все**. В следующем примере кода показано, как для установки удаленного доступа в мультитенантном режиме со всеми функциями удаленного доступа (типа "точка сеть" сеть сеть VPN и BGP маршрутизации) включена для двух клиентов: Contoso и Fabrikam.  
  
```  
$Contoso_RoutingDomain = "ContosoTenant"  
$Fabrikam_RoutingDomain = "FabrikamTenant"  
  
Install-RemoteAccess -MultiTenancy  
  
Enable-RemoteAccessRoutingDomain -Name $Contoso_RoutingDomain -Type All -PassThru  
Enable-RemoteAccessRoutingDomain -Name $Fabrikam_RoutingDomain -Type All -PassThru  
```  
  
При использовании удаленного доступа в качестве маршрутизатора локальной сети, а не как шлюз, можно по-прежнему использовать BGP, которая предоставляет преимущество с динамической маршрутизацией в интрасети. Для установки удаленного доступа в качестве маршрутизатора BGP локальной сети, введите следующую команду в командной строке Windows PowerShell и нажмите клавишу ВВОД.  
  
```  
Install-RemoteAccess -VpnType RoutingOnly  
```  
  
### <a name="bkmk_remove"></a>Удалить команды  
Ниже приведены команды удаления для BGP.  
  
[Remove-BgpCustomRoute](https://technet.microsoft.com/library/dn262669.aspx)  
  
Удаление настраиваемых маршрутов от маршрутизатора BGP.  
  
```  
Remove-BgpCustomRoute [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-Interface <String[]> ] [-Network <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Remove указано](https://technet.microsoft.com/library/dn262675.aspx)  
  
Удаляет узлы BGP из маршрутизатора.  
  
```  
Remove-BgpPeer [-Name] <String[]> [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Remove-BgpRouteAggregate](https://technet.microsoft.com/library/mt463110.aspx)  
  
Удаляет набор указанный агрегированные маршруты BGP.  
  
```  
Remove-BgpRouteAggregate [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-Prefix <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Remove-BgpRouter](https://technet.microsoft.com/library/dn262678.aspx)  
  
Удаляет маршрутизатор BGP.  
  
```  
Remove-BgpRouter [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String[]> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Remove-BgpRoutingPolicy](https://technet.microsoft.com/library/dn262656.aspx)  
  
Удаляет маршрут политик из хранилища политик.  
  
```  
Remove-BgpRoutingPolicy [-Name] <String[]> [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Remove-BgpRoutingPolicyForPeer](https://technet.microsoft.com/library/dn262681.aspx)  
  
Удаляет маршрут политики из узлов BGP.  
  
```  
Parameter Set: Remove1  
Remove-BgpRoutingPolicyForPeer [-CimSession <CimSession[]> ] [-Direction <PolicyDirection> {Ingress | Egress} ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-PeerName <String[]> ] [-PolicyName <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="bkmk_set"></a>Набор команд  
Ниже приведены команды Set для BGP.  
  
[SET указано](https://technet.microsoft.com/library/dn262673.aspx)  
  
Обновляет конфигурацию указанного узла BGP.  
  
```  
Set-BgpPeer [-Name] <String> [-CimSession <CimSession[]> ] [-ClearPrefixLimit] [-Force] [-HoldTimeSec <UInt16> ] [-IdleHoldTimeSec <UInt16> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-LocalASN <UInt32> ] [-LocalIPAddress <IPAddress> ] [-MaxAllowedPrefix <UInt32> ] [-OperationMode <OperationMode> {Mixed | Server} ] [-PassThru] [-PeerASN <UInt32> ] [-PeeringMode <PeeringMode> {Automatic | Manual} ] [-PeerIPAddress <IPAddress> ] [-RouteReflectorClient <Boolean> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Weight <UInt16> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[SET-BgpRouteAggregate](https://technet.microsoft.com/library/mt463115.aspx)  
  
Обновляет свойства указанной агрегатной маршрут BGP.  
  
```  
Set-BgpRouteAggregate -Prefix <String> [-AttributePolicy <String[]> ] [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-PassThru] [-PreserveASPath <PreserveASPath> ] [-RoutingDomain <String> ] [-SummaryOnly <SummaryOnly> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[SET-BgpRouteFlapDampening](https://technet.microsoft.com/library/mt463116.aspx)  
  
Настраивает гашение обработчик маршрута BGP.  
  
```  
Set-BgpRouteFlapDampening [-CimSession <CimSession[]> ] [-Force] [-HalfLife <UInt32> ] [-HalfLifeUnreachable <UInt32> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-MaxSuppressTime <UInt32> ] [-PassThru] [-ReuseThreshold <UInt32> ] [-RoutingDomain <String> ] [-SuppressThreshold <UInt32> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[SET-BgpRouter](https://technet.microsoft.com/library/dn262652.aspx)  
  
Обновляет конфигурацию локального маршрутизатора BGP для идентификатор указанного клиента.  
  
```  
Set-BgpRouter [-BgpIdentifier <IPAddress> ] [-CimSession <CimSession[]> ] [-ClientToClientReflection <ClientToClientReflection> ] [-ClusterId <UInt32> ] [-CompareMEDAcrossASN <Boolean> ] [-DefaultGatewayRouting <Boolean> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-IPv6Routing <IPv6RoutingState> {Disabled | Enabled} ] [-LocalASN <UInt32> ] [-LocalIPv6Address <IPAddress> ] [-PassThru] [-RouteReflector <RouteReflector> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-TransitRouting <TransitRouting> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[SET-BgpRoutingPolicy](https://technet.microsoft.com/library/dn262670.aspx)  
  
Изменение конфигурации маршрутизации с политики.  
  
```  
Set-BgpRoutingPolicy [-Name] <String> [-AddCommunity <String[]> ] [-CimSession <CimSession[]> ] [-ClearMED] [-Force] [-IgnorePrefix <String[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-MatchASNRange <UInt32[]> ] [-MatchCommunity <String[]> ] [-MatchNextHop <IPAddress[]> ] [-MatchPrefix <String[]> ] [-NewLocalPref <UInt32]> ] [-NewMED <UInt32]> ] [-NewNextHop <IPAddress> ] [-PassThru] [-PolicyType <PolicyType> {Deny | Allow | ModifyAttribute} ] [-RemoveAllCommunities] [-RemoveCommunity <String[]> ] [-RemovePolicyClause <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[SET-BgpRoutingPolicyForPeer](https://technet.microsoft.com/library/dn262674.aspx)  
  
Изменение политики маршрутизации BGP для узлов BGP.  
  
```  
Set-BgpRoutingPolicyForPeer -Direction <PolicyDirection> {Ingress | Egress} -PolicyName <String[]> [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-PeerName <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="bkmk_start"></a>Start и Stop команды  
Ниже приведены команды Start и Stop для BGP.  
  
[Start указано](https://technet.microsoft.com/library/dn262683.aspx)  
  
Запускает маршрутизации сеансы для узлов BGP.  
  
```  
Start-BgpPeer [-Name] <String[]> [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[STOP указано](https://technet.microsoft.com/library/dn262661.aspx)  
  
Останавливает маршрутизации сеансы для узлов BGP.  
  
```  
Stop-BgpPeer [-Name] <String[]> [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="bkmk_uninstall"></a>Команды удаления  
Ниже приведены команды удаления для шлюза RAS и BGP.  
  
[Удаление удаленного доступа](https://technet.microsoft.com/library/hh918390.aspx)  
  
Удаляет удаленный доступ с компьютера, включая все функции удаленного доступа и функциональные возможности (шлюз RAS, BGP и т. д).  
  
```  
Uninstall-RemoteAccess [-CimSession <CimSession[]> ] [-ComputerName <String> ] [-EntrypointName <String> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-ThrottleLimit <Int32> ] [-VpnType <String> {Vpn | VpnS2S} ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  


