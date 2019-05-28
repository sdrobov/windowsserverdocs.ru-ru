---
title: Настройка AD FS заблокированных IP-адреса
description: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 06/28/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 01ef992554a1e0961d8d795e9baa7730a1a1d682
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66189888"
---
# <a name="ad-fs-and-banned-ip-addresses"></a>AD FS и запрещенных IP-адресов


В июня 2018 г., AD FS на Windows Server 2016 появилась **заблокированных IP-адреса** в AD FS обновление июня 2018 г.  Это обновление позволяет настраивать набор IP-адресов глобально в AD FS, чтобы запросы, поступающие из этих IP-адресов, или у этих IP-адресов **x-forwarded-for** или **x-ms-forwarded--IP-адрес клиента** заголовки, будут блокироваться AD FS.

## <a name="adding-banned-ips"></a>Добавление заблокированных IP-адресов
Чтобы добавить глобальный список заблокированных IP-адресов, используйте ниже командлет Powershell:

``` powershell
PS C:\ >Set-AdfsProperties -AddBannedIps "1.2.3.4", "::3", "1.2.3.4/16"
```

Допустимые форматы

1.  IPv4
2.  IPv6
3.  Формат CIDR с IPv4- или версии 6

Ограничено 300 записей для заблокированных IP-адресов. Формат CIDR или диапазон можно использовать для запрета большой блок операций с одной записи.

## <a name="removing-banned-ips"></a>Удаление заблокированных IP-адресов
Чтобы удалить запрещенных IP-адресов из глобального списка, используйте ниже командлет Powershell:

``` powershell
PS C:\ >Set-AdfsProperties -RemoveBannedIps "1.2.3.4"
```

#### <a name="read-banned-ips"></a>Чтение заблокированных IP-адресов
Чтобы считать текущий набор запрещенных IP-адресов, используйте ниже командлет Powershell:

``` powershell
PS C:\ >Get-AdfsProperties 
```

Пример вывода команды:

```
BannedIpList                   : {1.2.3.4, ::3,1.2.3.4/16}
```



## <a name="additional-references"></a>Дополнительная справка  
[Рекомендации по обеспечению безопасности служб федерации Active Directory](../../ad-fs/deployment/best-practices-securing-ad-fs.md)

[Set-AdfsProperties](https://technet.microsoft.com/itpro/powershell/windows/adfs/set-adfsproperties)

[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)
