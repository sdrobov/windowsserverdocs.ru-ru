---
title: Настройка AD FS запрещенных IP-адресов
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 06/28/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 1a1e8a9e668caa0c766f6fe3012d5ae6ecaddb50
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859927"
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
