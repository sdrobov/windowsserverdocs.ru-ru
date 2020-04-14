---
title: Справочник по командам BGP для Windows PowerShell
description: Этот раздел можно использовать в качестве справочной документации при написании сценариев Windows PowerShell в Windows Server 2016 для добавления, настройки и удаления возможностей BGP из шлюза RAS и маршрутизаторов локальной сети удаленного доступа (LAN).
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: 4b0240a3-b927-4a1e-b241-5f8f29a9552f
ms.author: lizross
author: eross-msft
ms.openlocfilehash: e206ead9d4af53c0ee404eb5077c88fef2b87ba7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80815847"
---
# <a name="bgp-windows-powershell-command-reference"></a>Справочник по командам BGP для Windows PowerShell

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Этот раздел можно использовать в качестве справочной документации при написании сценариев Windows PowerShell для добавления, настройки и удаления возможностей BGP из шлюза RAS и маршрутизаторов локальной сети удаленного доступа (LAN).  
  
Эти команды BGP входят в набор команд Windows PowerShell для удаленного доступа для Windows Server 2016. Этот раздел поможет быстро находить команды BGP, которые нужно использовать в скриптах.  
  
Дополнительные сведения обо всех командах удаленного доступа см. в разделе [Командлеты удаленного доступа](https://technet.microsoft.com/library/hh918399.aspx).  
  
## <a name="bgp-command-reference"></a>Справочник по командам BGP  
В следующих разделах приводятся имя команды, назначение и синтаксис для каждой команды BGP, а также ссылка на команду в справочнике по удаленному доступу, в которой содержатся более подробные сведения о каждой команде.  
  
Этот справочный материал содержит следующие разделы.  
  
-   [Добавить команды](#bkmk_add)  
  
-   [Очистить команды](#bkmk_clear)  
  
-   [Отключение и включение команд](#bkmk_disable)  
  
-   [Получение команд](#bkmk_get)  
  
-   [Команды установки](#bkmk_install)  
  
-   [Удалить команды](#bkmk_remove)  
  
-   [Команды Set](#bkmk_set)  
  
-   [Команды запуска и завершения](#bkmk_start)  
  
-   [Команды удаления](#bkmk_uninstall)  
  
### <a name="add-commands"></a><a name="bkmk_add"></a>Добавить команды  
Ниже приведены команды BGP Add.  
  
[Add-Бгпкустомрауте](https://technet.microsoft.com/library/dn262684.aspx)  
  
Добавляет пользовательские маршруты в таблицу маршрутизации BGP.  
  
```  
Add-BgpCustomRoute [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-Interface <String[]> ] [-Network <String[]> ] [-PassThru] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Add-BgpPeer](https://technet.microsoft.com/library/dn262687.aspx)  
  
Добавляет новый узел BGP.  
  
```  
Add-BgpPeer [-Name] <String> -LocalIPAddress <IPAddress> -PeerASN <UInt32> -PeerIPAddress <IPAddress> [-CimSession <CimSession[]> ] [-HoldTimeSec <UInt16> ] [-IdleHoldTimeSec <UInt16> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-LocalASN <UInt32> ] [-MaxAllowedPrefix <UInt32> ] [-OperationMode <OperationMode> {Mixed | Server} ] [-PassThru] [-PeeringMode <PeeringMode> {Automatic | Manual} ] [-RouteReflectorClient <Boolean> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Weight <UInt16> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Add-Бгпраутеаггрегате](https://technet.microsoft.com/library/mt463113.aspx)  
  
Добавляет новый статистический маршрут для конкретных маршрутов BGP.  
  
```  
Add-BgpRouteAggregate -Prefix <String> [-AttributePolicy <String[]> ] [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-PassThru] [-PreserveASPath <PreserveASPath> ] [-RoutingDomain <String> ] [-SummaryOnly <SummaryOnly> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Add-Бгпраутер](https://technet.microsoft.com/library/dn262665.aspx)  
  
Добавляет маршрутизатор BGP для указанного идентификатора клиента.  
  
```  
Add-BgpRouter -BgpIdentifier <IPAddress> -LocalASN <UInt32> [-CimSession <CimSession[]> ] [-ClientToClientReflection <ClientToClientReflection> ] [-ClusterId <UInt32> ] [-CompareMEDAcrossASN <Boolean> ] [-DefaultGatewayRouting <Boolean> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-IPv6Routing <IPv6RoutingState> {Disabled | Enabled} ] [-LocalIPv6Address <IPAddress> ] [-PassThru] [-RouteReflector <RouteReflector> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-TransitRouting <TransitRouting> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Add-Бгпраутингполици](https://technet.microsoft.com/library/dn262662.aspx)  
  
Добавляет политику маршрутизации BGP в хранилище политик.  
  
```  
Add-BgpRoutingPolicy [-Name] <String> [-PolicyType] <PolicyType> {Deny | Allow | ModifyAttribute} [-AddCommunity <String[]> ] [-CimSession <CimSession[]> ] [-ClearMED] [-Force] [-IgnorePrefix <String[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-MatchASNRange <UInt32[]> ] [-MatchCommunity <String[]> ] [-MatchNextHop <IPAddress[]> ] [-MatchPrefix <String[]> ] [-NewLocalPref <UInt32]> ] [-NewMED <UInt32]> ] [-NewNextHop <IPAddress> ] [-PassThru] [-RemoveAllCommunities] [-RemoveCommunity <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Add-Бгпраутингполицифорпир](https://technet.microsoft.com/library/dn262680.aspx)  
  
Добавляет политики маршрутизации BGP к одноранговым узлам BGP.  
  
```  
Add-BgpRoutingPolicyForPeer -Direction <PolicyDirection> {Ingress | Egress} -PolicyName <String[]> [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-PeerName <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="clear-commands"></a><a name="bkmk_clear"></a>Очистить команды  
Ниже приведены команды Clear для BGP.  
  
[Clear-Бгпраутефлапдампенинг](https://technet.microsoft.com/library/mt463114.aspx)  
  
Очищает сведения о ослаблении колыханий маршрута для указанного набора маршрутов BGP.  
  
```  
Clear-BgpRouteFlapDampening [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-Prefix <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="disable-and-enable-commands"></a><a name="bkmk_disable"></a>Отключение и включение команд  
Ниже приведены команды Disable и Enable для BGP.  
  
[Disable-Бгпраутефлапдампенинг](https://technet.microsoft.com/library/mt463100.aspx)  
  
Отключает ослабление маршрута для маршрутов BGP неустойчивый.  
  
```  
Disable-BgpRouteFlapDampening [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Enable-Бгпраутефлапдампенинг](https://technet.microsoft.com/library/mt463102.aspx)  
  
Включает ослабление маршрута для маршрутов BGP неустойчивый.  
  
```  
Enable-BgpRouteFlapDampening [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-PassThru] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="get-commands"></a><a name="bkmk_get"></a>Получение команд  
Ниже приведены команды Get для BGP.  
  
[Get-Бгпкустомрауте](https://technet.microsoft.com/library/dn262664.aspx)  
  
Получает настраиваемые сведения о маршруте от маршрутизатора BGP.  
  
```  
Get-BgpCustomRoute [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-BgpPeer](https://technet.microsoft.com/library/dn262659.aspx)  
  
Возвращает сведения о конфигурации для узлов BGP.  
  
```  
Get-BgpPeer [[-Name] <String[]> ] [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-Бгпраутеаггрегате](https://technet.microsoft.com/library/mt463103.aspx)  
  
Возвращает все сводные маршруты BGP, настроенные администратором.  
  
```  
Get-BgpRouteAggregate [-CimSession <CimSession[]> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-Prefix <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-Бгпраутефлапдампенинг](https://technet.microsoft.com/library/mt463108.aspx)  
  
Извлекает конфигурацию подсистемы ослабления маршрута BGP.  
  
```  
Get-BgpRouteFlapDampening [-CimSession <CimSession[]> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-Бгпраутеинформатион](https://technet.microsoft.com/library/dn262667.aspx)  
  
Получает сведения о маршруте BGP для одного или нескольких префиксов сети из таблицы маршрутизации BGP.  
  
```  
Get-BgpRouteInformation [-CimSession <CimSession[]> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-Network <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Type <RouteType> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-Бгпраутер](https://technet.microsoft.com/library/dn262660.aspx)  
  
Возвращает сведения о конфигурации маршрутизаторов BGP.  
  
```  
Get-BgpRouter [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String[]> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-Бгпраутингполици](https://technet.microsoft.com/library/dn262672.aspx)  
  
Возвращает сведения о конфигурации политик маршрутизации BGP.  
  
```  
Get-BgpRoutingPolicy [[-Name] <String[]> ] [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-PolicyType <PolicyType> {Deny | Allow | ModifyAttribute} ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Get-Бгпстатистикс](https://technet.microsoft.com/library/dn262685.aspx)  
  
Извлекает связанное с пирингом BGP сообщение и статистику объявлений маршрутов.  
  
```  
Get-BgpStatistics [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-PeerName <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="install-commands"></a><a name="bkmk_install"></a>Команды установки  
Ниже приведены команды установки для шлюза RAS и BGP.  
  
[Install-RemoteAccess](https://technet.microsoft.com/library/hh918408.aspx)  
  
Выполняет проверки готовности для DirectAccess (DA), чтобы убедиться, что она может быть установлена, устанавливает DA для удаленного доступа (RA) (включая управление удаленными клиентами) или только для управления удаленными клиентами, устанавливает VPN (VPN удаленного доступа и VPN типа "сеть-сеть"). и устанавливает маршрутизацию BGP.  
  
```  
Parameter Set: MultiTenant  
Install-RemoteAccess [-MultiTenancy] [-CapacityKbps <UInt64> ] [-CimSession <CimSession[]> ] [-ComputerName <String> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-MsgAuthenticator <String> {Enabled | Disabled} ] [-PassThru] [-RadiusPort <UInt16> ] [-RadiusScore <Byte> ] [-RadiusServer <String> ] [-RadiusTimeout <UInt32> ] [-SharedSecret <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
  
Parameter Set: Vpn  
Install-RemoteAccess [-VpnType] <String> {Vpn | VpnS2S | SstpProxy | RoutingOnly} [-CimSession <CimSession[]> ] [-ComputerName <String> ] [-EntrypointName <String> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-IPAddressRange <String[]> ] [-IPv6Prefix <String> ] [-Legacy] [-MsgAuthenticator <String> {Enabled | Disabled} ] [-PassThru] [-RadiusPort <UInt16> ] [-RadiusScore <Byte> ] [-RadiusServer <String> ] [-RadiusTimeout <UInt32> ] [-SharedSecret <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
> [!IMPORTANT]  
> При установке шлюза RAS в многоклиентский режим необходимо указать, включен ли протокол BGP для каждого клиента с помощью команды Windows PowerShell **Enable-ремотеакцессраутингдомаин** с параметром **-Type** со значением **ALL**. В следующем примере кода показано, как установить RAS в режиме многоадресной рассылки со всеми компонентами удаленного доступа (VPN-подключение типа "точка — сеть", VPN-подключением типа "сеть — сеть" и маршрутизацией BGP) для двух клиентов, Contoso и Fabrikam.  
  
```  
$Contoso_RoutingDomain = "ContosoTenant"  
$Fabrikam_RoutingDomain = "FabrikamTenant"  
  
Install-RemoteAccess -MultiTenancy  
  
Enable-RemoteAccessRoutingDomain -Name $Contoso_RoutingDomain -Type All -PassThru  
Enable-RemoteAccessRoutingDomain -Name $Fabrikam_RoutingDomain -Type All -PassThru  
```  
  
Если вы используете удаленный доступ в качестве маршрутизатора локальной сети, а не шлюза, вы по-прежнему можете использовать BGP, который предоставляет преимущества динамической маршрутизации в интрасети. Чтобы установить удаленный доступ в качестве маршрутизатора локальной сети BGP, введите следующую команду в командной строке Windows PowerShell и нажмите клавишу ВВОД.  
  
```  
Install-RemoteAccess -VpnType RoutingOnly  
```  
  
### <a name="remove-commands"></a><a name="bkmk_remove"></a>Удалить команды  
Ниже приведены команды Remove для BGP.  
  
[Remove-Бгпкустомрауте](https://technet.microsoft.com/library/dn262669.aspx)  
  
Удаляет настраиваемые маршруты из маршрутизатора BGP.  
  
```  
Remove-BgpCustomRoute [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-Interface <String[]> ] [-Network <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Remove-BgpPeer](https://technet.microsoft.com/library/dn262675.aspx)  
  
Удаляет узлы BGP с маршрутизатора.  
  
```  
Remove-BgpPeer [-Name] <String[]> [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Remove-Бгпраутеаггрегате](https://technet.microsoft.com/library/mt463110.aspx)  
  
Удаляет набор указанных статистических маршрутов BGP.  
  
```  
Remove-BgpRouteAggregate [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-Prefix <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Remove-Бгпраутер](https://technet.microsoft.com/library/dn262678.aspx)  
  
Удаляет маршрутизатор BGP.  
  
```  
Remove-BgpRouter [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String[]> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Remove-Бгпраутингполици](https://technet.microsoft.com/library/dn262656.aspx)  
  
Удаляет политики маршрутизации из хранилища политик.  
  
```  
Remove-BgpRoutingPolicy [-Name] <String[]> [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Remove-Бгпраутингполицифорпир](https://technet.microsoft.com/library/dn262681.aspx)  
  
Удаляет политики маршрутизации с узлов BGP.  
  
```  
Parameter Set: Remove1  
Remove-BgpRoutingPolicyForPeer [-CimSession <CimSession[]> ] [-Direction <PolicyDirection> {Ingress | Egress} ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-PeerName <String[]> ] [-PolicyName <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="set-commands"></a><a name="bkmk_set"></a>Команды Set  
Ниже приведены команды Set для BGP.  
  
[Set-BgpPeer](https://technet.microsoft.com/library/dn262673.aspx)  
  
Обновляет конфигурацию указанного узла BGP.  
  
```  
Set-BgpPeer [-Name] <String> [-CimSession <CimSession[]> ] [-ClearPrefixLimit] [-Force] [-HoldTimeSec <UInt16> ] [-IdleHoldTimeSec <UInt16> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-LocalASN <UInt32> ] [-LocalIPAddress <IPAddress> ] [-MaxAllowedPrefix <UInt32> ] [-OperationMode <OperationMode> {Mixed | Server} ] [-PassThru] [-PeerASN <UInt32> ] [-PeeringMode <PeeringMode> {Automatic | Manual} ] [-PeerIPAddress <IPAddress> ] [-RouteReflectorClient <Boolean> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Weight <UInt16> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Set-Бгпраутеаггрегате](https://technet.microsoft.com/library/mt463115.aspx)  
  
Обновляет свойства указанного статистического маршрута BGP.  
  
```  
Set-BgpRouteAggregate -Prefix <String> [-AttributePolicy <String[]> ] [-CimSession <CimSession[]> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-PassThru] [-PreserveASPath <PreserveASPath> ] [-RoutingDomain <String> ] [-SummaryOnly <SummaryOnly> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Set-Бгпраутефлапдампенинг](https://technet.microsoft.com/library/mt463116.aspx)  
  
Настраивает подсистему ослабления маршрута BGP.  
  
```  
Set-BgpRouteFlapDampening [-CimSession <CimSession[]> ] [-Force] [-HalfLife <UInt32> ] [-HalfLifeUnreachable <UInt32> ] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-MaxSuppressTime <UInt32> ] [-PassThru] [-ReuseThreshold <UInt32> ] [-RoutingDomain <String> ] [-SuppressThreshold <UInt32> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Set-Бгпраутер](https://technet.microsoft.com/library/dn262652.aspx)  
  
Обновляет конфигурацию локального маршрутизатора BGP для указанного идентификатора клиента.  
  
```  
Set-BgpRouter [-BgpIdentifier <IPAddress> ] [-CimSession <CimSession[]> ] [-ClientToClientReflection <ClientToClientReflection> ] [-ClusterId <UInt32> ] [-CompareMEDAcrossASN <Boolean> ] [-DefaultGatewayRouting <Boolean> ] [-Force] [-InformationAction <ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <String> ] [-IPv6Routing <IPv6RoutingState> {Disabled | Enabled} ] [-LocalASN <UInt32> ] [-LocalIPv6Address <IPAddress> ] [-PassThru] [-RouteReflector <RouteReflector> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-TransitRouting <TransitRouting> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Set-Бгпраутингполици](https://technet.microsoft.com/library/dn262670.aspx)  
  
Изменяет конфигурацию политики маршрутизации.  
  
```  
Set-BgpRoutingPolicy [-Name] <String> [-AddCommunity <String[]> ] [-CimSession <CimSession[]> ] [-ClearMED] [-Force] [-IgnorePrefix <String[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-MatchASNRange <UInt32[]> ] [-MatchCommunity <String[]> ] [-MatchNextHop <IPAddress[]> ] [-MatchPrefix <String[]> ] [-NewLocalPref <UInt32]> ] [-NewMED <UInt32]> ] [-NewNextHop <IPAddress> ] [-PassThru] [-PolicyType <PolicyType> {Deny | Allow | ModifyAttribute} ] [-RemoveAllCommunities] [-RemoveCommunity <String[]> ] [-RemovePolicyClause <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[Set-Бгпраутингполицифорпир](https://technet.microsoft.com/library/dn262674.aspx)  
  
Изменяет политики маршрутизации BGP для узлов BGP.  
  
```  
Set-BgpRoutingPolicyForPeer -Direction <PolicyDirection> {Ingress | Egress} -PolicyName <String[]> [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-PeerName <String[]> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="start-and-stop-commands"></a><a name="bkmk_start"></a>Команды запуска и завершения  
Ниже приведены команды запуска и завершения для BGP.  
  
[Start-BgpPeer](https://technet.microsoft.com/library/dn262683.aspx)  
  
Запускает маршрутизацию сеансов для узлов BGP.  
  
```  
Start-BgpPeer [-Name] <String[]> [-CimSession <CimSession[]> ] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
[BgpPeer](https://technet.microsoft.com/library/dn262661.aspx)  
  
Останавливает маршрутизацию сеансов для узлов BGP.  
  
```  
Stop-BgpPeer [-Name] <String[]> [-CimSession <CimSession[]> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-RoutingDomain <String> ] [-ThrottleLimit <Int32> ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  
### <a name="uninstall-commands"></a><a name="bkmk_uninstall"></a>Команды удаления  
Ниже приведены команды удаления для шлюза RAS и BGP.  
  
[Uninstall-RemoteAccess](https://technet.microsoft.com/library/hh918390.aspx)  
  
Удаляет удаленный доступ с компьютера, включая все компоненты и функции удаленного доступа (шлюз RAS, BGP и т. д.).  
  
```  
Uninstall-RemoteAccess [-CimSession <CimSession[]> ] [-ComputerName <String> ] [-EntrypointName <String> ] [-Force] [-InformationAction <System.Management.Automation.ActionPreference> {SilentlyContinue | Stop | Continue | Inquire | Ignore | Suspend} ] [-InformationVariable <System.String> ] [-ThrottleLimit <Int32> ] [-VpnType <String> {Vpn | VpnS2S} ] [-Confirm] [-WhatIf] [ <CommonParameters>] [ <WorkflowParameters>]  
```  
  


