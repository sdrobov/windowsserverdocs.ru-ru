---
title: Ролевое управление доступом с помощью Windows PowerShell
description: Этот раздел входит руководство по управлению управления IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f13f78e-0114-4e41-9a28-82a4feccecfc
ms.author: pashort
author: shortpatti
ms.openlocfilehash: df6fa423a4ec891f1ad3faefad6c6054519542c4
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="manage-role-based-access-control-with-windows-powershell"></a>Ролевое управление доступом с помощью Windows PowerShell

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать, чтобы узнать, как с помощью IPAM для управления доступом на основе ролей с помощью Windows PowerShell.  
  
>[!NOTE]
>Справочник по командам IPAM Windows PowerShell в разделе [командлеты сервер управления IP-адресами (IPAM) в Windows PowerShell](https://technet.microsoft.com/library/jj553807.aspx).  
  
Новые команды Windows PowerShell IPAM предоставляют возможность получения и изменения области доступа объектов DNS и DHCP. В следующей таблице показан правильный команду, чтобы использовать для каждого объекта IPAM.  
  
|Объект IPAM|Команда|Описание|  
|---------------|-----------|---------------|  
|DNS-сервера|Get-IpamDnsServer|Этот командлет возвращает объект DNS-сервер в IPAM|  
|Зоны DNS|Get-IpamDnsZone|Этот командлет возвращает объект зоны DNS в IPAM|  
|Запись ресурса DNS|Get-IpamResourceRecord|Этот командлет возвращает объект записи ресурсов DNS в IPAM|  
|Сервер условной пересылки DNS-сервера|Get-IpamDnsConditionalForwarder|Этот командлет возвращает объект условного сервера пересылки DNS-сервера в IPAM|  
|DHCP-сервера|Get-IpamDhcpServer|Этот командлет возвращает объект DHCP-сервера в IPAM|  
|Суперобласти DHCP|Get-IpamDhcpSuperscope|Этот командлет возвращает объект суперобласти DHCP в IPAM|  
|Области DHCP|Get-IpamDhcpScope|Этот командлет возвращает объект области DHCP в IPAM|  
  
В следующем примере выходных данных команды `Get-IpamDnsZone` командлет извлекает **dublin.contoso.com** зоны DNS.  
  
```  
PS C:\Users\Administrator.CONTOSO> Get-IpamDnsZone -ZoneType Forward -ZoneName dublin.contoso.com  
  
ZoneName             : dublin.contoso.com  
ZoneType             : Forward  
AccessScopePath      : \Global\Dublin  
IsSigned             : False  
DynamicUpdateStatus  : None  
ScavengeStaleRecords : False  
```  
  
## <a name="setting-access-scopes-on-ipam-objects"></a>Задание области доступа для объектов IPAM  
Можно задать области доступа IPAM объектов с помощью `Set-IpamAccessScope` команды. Эта команда используется для задания области доступа конкретное значение объекта или вызвать объекты наследовать область доступа от родительских объектов. Ниже приведены объекты, которые можно настроить с помощью следующей команды.  
  
-   Области DHCP  
  
-   DHCP-сервера  
  
-   Суперобласти DHCP  
  
-   Сервер условной пересылки DNS-сервера  
  
-   Записи ресурсов DNS  
  
-   DNS-сервера  
  
-   Зоны DNS  
  
-   Блок IP-адресов  
  
-   Диапазон IP-адресов  
  
-   Пространство IP-адресов  
  
-   Подсеть IP-адресов  
  
Ниже приведен синтаксис `Set-IpamAccessScope` команды.  
  
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
  
В следующем примере область доступа зоны DNS **dublin.contoso.com** меняется с **Dublin** для **Europe**.  
  
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
  


