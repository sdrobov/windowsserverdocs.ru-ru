---
title: Настройка AD FS запрещенных IP-адресов
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 06/28/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 9e38105bafc92efc4d9e62e4815cdb24c3c25512
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965616"
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

Выходные данные примера:

```
BannedIpList                   : {1.2.3.4, ::3,1.2.3.4/16}
```



## <a name="additional-references"></a>Дополнительные ссылки  
[Рекомендации по обеспечению безопасности службы федерации Active Directory (AD FS)](../../ad-fs/deployment/best-practices-securing-ad-fs.md)

[Set-AdfsProperties](/powershell/module/adfs/set-adfsproperties?view=win10-ps)

[Операции AD FS](../ad-fs-operations.md)
