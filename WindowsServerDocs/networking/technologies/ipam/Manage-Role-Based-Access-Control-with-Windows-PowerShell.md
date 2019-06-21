---
title: Контроль управления доступом на основе ролей с помощью Windows PowerShell
description: Этот раздел является частью в руководстве по управления IP Address Management (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f13f78e-0114-4e41-9a28-82a4feccecfc
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 11dd417be4720b09851fc03f111edaaf06b55e59
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67282136"
---
# <a name="manage-role-based-access-control-with-windows-powershell"></a>Контроль управления доступом на основе ролей с помощью Windows PowerShell

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Чтобы узнать, как с помощью IPAM для управления доступом на основе ролей с помощью Windows PowerShell можно использовать в этом разделе.  
  
>[!NOTE]
>Справочник по командам IPAM Windows PowerShell, см. в разделе [IpamServer командлетов в Windows PowerShell](https://docs.microsoft.com/powershell/module/ipamserver/?view=win10-ps).  
  
Новые команды Windows PowerShell IPAM дают возможность извлечения и изменения области доступа объектов DNS и DHCP. В следующей таблице показано нужную команду для каждого объекта IPAM.  
  
|Объект IPAM|Command|Описание|  
|---------------|-----------|---------------|  
|DNS-сервер|Get-IpamDnsServer|Этот командлет возвращает объект DNS-сервер в IPAM|  
|Зона DNS|Get-IpamDnsZone|Этот командлет возвращает объект зоны DNS в IPAM|  
|DNS Resource Record|Get-IpamResourceRecord|Этот командлет возвращает объект записи ресурсов DNS в IPAM|  
|Сервер условной пересылки DNS|Get-IpamDnsConditionalForwarder|Этот командлет возвращает объект сервер условной пересылки DNS в IPAM|  
|DHCP-сервер|Get-IpamDhcpServer|Этот командлет возвращает объект сервера DHCP в IPAM|  
|Суперобласть DHCP|Get-IpamDhcpSuperscope|Этот командлет возвращает объект суперобласти DHCP в IPAM|  
|Область DHCP|Get-IpamDhcpScope|Этот командлет возвращает объект области DHCP в IPAM|  
  
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
  
## <a name="setting-access-scopes-on-ipam-objects"></a>Задание области доступа в объектах IPAM  
Можно задать области доступа IPAM объектов с помощью `Set-IpamAccessScope` команды. Эта команда используется для задания области доступа конкретное значение для объекта или, чтобы вызвать объекты наследовать область доступа от родительских объектов. Ниже перечислены объекты, которые можно настроить с помощью следующей команды.  
  
-   Область DHCP  
  
-   DHCP-сервер  
  
-   Суперобласть DHCP  
  
-   Сервер условной пересылки DNS  
  
-   DNS Resource Records  
  
-   DNS-сервер  
  
-   Зона DNS  
  
-   Блокировка IP-адресов  
  
-   Диапазон IP-адресов  
  
-   Пространство IP-адресов  
  
-   Подсеть IP-адресов  
  
Ниже приведен синтаксис для `Set-IpamAccessScope` команды.  
  
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
  
В следующем примере область доступа зоны DNS **dublin.contoso.com** меняется с **Dublin** для **Европа**.  
  
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
  


