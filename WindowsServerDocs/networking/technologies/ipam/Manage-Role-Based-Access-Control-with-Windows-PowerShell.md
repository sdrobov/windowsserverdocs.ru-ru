---
title: Контроль управления доступом на основе ролей с помощью Windows PowerShell
description: Этот раздел является частью руководства по управлению IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f13f78e-0114-4e41-9a28-82a4feccecfc
ms.author: lizross
author: eross-msft
ms.openlocfilehash: a5cd347b849948052f4f7caa7fa8a863808e8c26
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80309538"
---
# <a name="manage-role-based-access-control-with-windows-powershell"></a>Контроль управления доступом на основе ролей с помощью Windows PowerShell

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

С помощью этого раздела вы узнаете, как использовать IPAM для управления доступом на основе ролей с помощью Windows PowerShell.  
  
>[!NOTE]
>Справочник по командам Windows PowerShell для IPAM см. в разделе [командлеты ипамсервер в Windows PowerShell](https://docs.microsoft.com/powershell/module/ipamserver/?view=win10-ps).  
  
Новые команды Windows PowerShell IPAM предоставляют возможность извлечения и изменения областей доступа объектов DNS и DHCP. В следующей таблице показана правильная команда, используемая для каждого объекта IPAM.  
  
|Объект IPAM|Команда|Описание|  
|---------------|-----------|---------------|  
|DNS-сервер|Get-Ипамднссервер|Этот командлет возвращает объект DNS-сервера в IPAM|  
|Зона DNS|Get-Ипамднсзоне|Этот командлет возвращает объект зоны DNS в IPAM|  
|Запись ресурса DNS|Get-Ипамресаурцерекорд|Этот командлет возвращает объект записи ресурсов DNS в IPAM|  
|DNS-сервер условной пересылки|Get-Ипамднскондитионалфорвардер|Этот командлет возвращает DNS-объект условной пересылки в IPAM|  
|DHCP-сервер|Get-Ипамдхкпсервер|Этот командлет возвращает объект DHCP-сервера в IPAM|  
|Суперобласть DHCP|Get-Ипамдхкпсуперскопе|Этот командлет возвращает объект суперобласти DHCP в IPAM|  
|Область DHCP|Get-Ипамдхкпскопе|Этот командлет возвращает объект области DHCP в IPAM|  
  
В следующем примере выходных данных команды командлет `Get-IpamDnsZone` извлекает зону DNS **Dublin.contoso.com** .  
  
```  
PS C:\Users\Administrator.CONTOSO> Get-IpamDnsZone -ZoneType Forward -ZoneName dublin.contoso.com  
  
ZoneName             : dublin.contoso.com  
ZoneType             : Forward  
AccessScopePath      : \Global\Dublin  
IsSigned             : False  
DynamicUpdateStatus  : None  
ScavengeStaleRecords : False  
```  
  
## <a name="setting-access-scopes-on-ipam-objects"></a>Настройка областей доступа для объектов IPAM  
Области доступа для объектов IPAM можно задать с помощью команды `Set-IpamAccessScope`. С помощью этой команды можно задать в качестве области доступа конкретное значение для объекта или сделать так, чтобы объекты наследовали область доступа от родительских объектов. Ниже приведены объекты, которые можно настроить с помощью этой команды.  
  
-   Область DHCP  
  
-   DHCP-сервер  
  
-   Суперобласть DHCP  
  
-   DNS-сервер условной пересылки  
  
-   Записи ресурсов DNS  
  
-   DNS-сервер  
  
-   Зона DNS  
  
-   Блокировка IP-адресов  
  
-   Диапазон IP-адресов  
  
-   Пространство IP-адресов  
  
-   Подсеть IP-адресов  
  
Ниже приведен синтаксис команды `Set-IpamAccessScope`.  
  
```  
NAME  
    Set-IpamAccessScope  
  
SYNTAX  
    Set-IpamAccessScope [-IpamRange] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDnsServer] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDhcpServer] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDhcpSuperscope] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDhcpScope] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDnsConditionalForwarder] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDnsResourceRecord] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamDnsZone] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamAddressSpace] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  
    [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamSubnet] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]  
  
    Set-IpamAccessScope [-IpamBlock] -InputObject <ciminstance[]> [-AccessScopePath <string>] [-IsInheritedAccessScope] [-PassThru] [-CimSession <CimSession[]>] [-ThrottleLimit <int>] [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]  
```  
  
В следующем примере область доступа зоны DNS **Dublin.contoso.com** изменяется с **Дублин** на **Европа**.  
  
```  
PS C:\Users\Administrator.CONTOSO> Get-IpamDnsZone -ZoneType Forward -ZoneName dublin.contoso.com  
  
ZoneName             : dublin.contoso.com  
ZoneType             : Forward  
AccessScopePath      : \Global\Dublin  
IsSigned             : False  
DynamicUpdateStatus  : None  
ScavengeStaleRecords : False  
  
PS C:\Users\Administrator.CONTOSO> $a = Get-IpamDnsZone -ZoneType Forward -ZoneName dublin.contoso.com  
PS C:\Users\Administrator.CONTOSO> Set-IpamAccessScope -IpamDnsZone -InputObject $a -AccessScopePath \Global\Europe -PassThru  
  
ZoneName             : dublin.contoso.com  
ZoneType             : Forward  
AccessScopePath      : \Global\Europe  
IsSigned             : False  
DynamicUpdateStatus  : None  
ScavengeStaleRecords : False  
```  
  


