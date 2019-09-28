---
title: Настройка AD FS запрещенных IP-адресов
description: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 06/28/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 2b518f92f80d06e4bd0854fde94013a412aae515
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407710"
---
# <a name="ad-fs-and-banned-ip-addresses"></a>AD FS и запрещенные IP-адреса


В июне 2018 AD FS на Windows Server 2016 предоставила **запрещенные IP-адреса** AD FS Июнь 2018.  Это обновление позволяет настроить набор IP-адресов глобально в AD FS, чтобы запросы, поступающие с этих IP-адресов, или IP-адреса из заголовков **x и** **MS-Forwarded-Client-IP** были заблокированы AD FS.

## <a name="adding-banned-ips"></a>Добавление запрещенных IP-адресов
Чтобы добавить запрещенные IP-адреса в глобальный список, используйте следующий командлет PowerShell:

``` powershell
PS C:\ >Set-AdfsProperties -AddBannedIps "1.2.3.4", "::3", "1.2.3.4/16"
```

Разрешенные форматы

1.  IPv4
2.  IPv6
3.  Формат CIDR с IPv4 или V6

Существует ограничение в 300 записей для запрещенных IP-адресов. Можно использовать CIDR или формат диапазона для запрета большого блока записей с одной записью.

## <a name="removing-banned-ips"></a>Удаление запрещенных IP-адресов
Чтобы удалить запрещенные IP-адреса из глобального списка, используйте следующий командлет PowerShell:

``` powershell
PS C:\ >Set-AdfsProperties -RemoveBannedIps "1.2.3.4"
```

#### <a name="read-banned-ips"></a>Чтение запрещенных IP-адресов
Чтобы прочитать текущий набор запрещенных IP-адресов, используйте следующий командлет PowerShell:

``` powershell
PS C:\ >Get-AdfsProperties 
```

Пример вывода команды:

```
BannedIpList                   : {1.2.3.4, ::3,1.2.3.4/16}
```



## <a name="additional-references"></a>Дополнительная справка  
[Рекомендации по обеспечению безопасности службы федерации Active Directory (AD FS)](../../ad-fs/deployment/best-practices-securing-ad-fs.md)

[Set-AdfsProperties](https://technet.microsoft.com/itpro/powershell/windows/adfs/set-adfsproperties)

[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)
