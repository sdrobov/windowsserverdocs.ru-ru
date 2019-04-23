---
title: ksetup
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e046f8a-811b-48dc-9a69-18d8e097f353
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0194cf81d069d7a5c1223f0a514d593e4870d397
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868845"
---
# <a name="ksetup"></a>ksetup



Выполняет задачи, связанные с настройкой и обслуживанием протокол Kerberos и центр распространения ключей (KDC) для поддержки сфер Kerberos, которые не являются также домены Windows. Примеры использования этой команды см. в разделе в подразделе примеров в каждой из связанных подразделов.

## <a name="syntax"></a>Синтаксис

```
ksetup 
[/setrealm <DNSDomainName>] 
[/mapuser <Principal> <Account>] 
[/addkdc <RealmName> <KDCName>] 
[/delkdc <RealmName> <KDCName>]
[/addkpasswd <RealmName> <KDCPasswordName>] 
[/delkpasswd <RealmName> <KDCPasswordName>]
[/server <ServerName>] 
[/setcomputerpassword <Password>]
[/removerealm <RealmName>]  
[/domain <DomainName>] 
[/changepassword <OldPassword> <NewPassword>] 
[/listrealmflags] 
[/setrealmflags <RealmName> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]] 
[/addrealmflags <RealmName> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]] 
[/delrealmflags [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]] 
[/dumpstate]
[/addhosttorealmmap] <HostName> <RealmName>]  
[/delhosttorealmmap] <HostName> <RealmName>]  
[/setenctypeattr] <DomainName> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
[/getenctypeattr] <DomainName>
[/addenctypeattr] <DomainName> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
[/delenctypeattr] <DomainName>

```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[ksetup:setrealm](ksetup-setrealm.md)|Этот компьютер становится членом областью Kerberos.|
|[ksetup:mapuser](ksetup-mapuser.md)|Сопоставляет субъектом Kerberos учетной записи.|
|[ksetup:addkdc](ksetup-addkdc.md)|Определяет запись центра распространения КЛЮЧЕЙ для данной области.|
|[ksetup:delkdc](ksetup-delkdc.md)|Удаление элемента KDC сферы.|
|[ksetup:addkpasswd](ksetup-addkpasswd.md)|Добавляет адрес сервера Kpasswd для сферы.|
|[ksetup:delkpasswd](ksetup-delkpasswd.md)|Удаляет адрес сервера Kpasswd для сферы.|
|[ksetup:Server](ksetup-server.md)|Позволяет указать имя компьютера Windows, к которому следует применить изменения.|
|[ksetup:setcomputerpassword](ksetup-setcomputerpassword.md)|Задает пароль для компьютера домена учетной записи (или участника узла).|
|[ksetup:removerealm](ksetup-removerealm.md)|Удаляет всю информацию для указанной области из реестра.|
|[ksetup:domain](ksetup-domain.md)|Можно указать домен (если \<DomainName > не было задано с помощью **/domain**).|
|[ksetup:ChangePassword](ksetup-changepassword.md)|Позволяет использовать Kpasswd для изменения пароля пользователя, вошедшего в систему.|
|[ksetup:listrealmflags](ksetup-listrealmflags.md)|Перечисляет доступные флаги сферы, **ksetup** может обнаружить.|
|[ksetup:setrealmflags](ksetup-setrealmflags.md)|Задает флаги сферы для определенной области.|
|[ksetup:addrealmflags](ksetup-addrealmflags.md)|Добавляет флаги сферы дополнительные области.|
|[ksetup:delrealmflags](ksetup-delrealmflags.md)|Удаляет флаги сферы из сферы.|
|[ksetup:dumpstate](ksetup-dumpstate.md)|Анализирует конфигурацию Kerberos на заданном компьютере. Добавляет узел в области сопоставления в реестр.|
|[ksetup:addhosttorealmmap](ksetup-addhosttorealmmap.md)|Добавляет значение реестра для сопоставления узла к области Kerberos.|
|[ksetup:delhosttorealmmap](ksetup-delhosttorealmmap.md)|Удаляет параметр реестра, который сопоставляется с главного компьютера области Kerberos.|
|[ksetup:setenctypeattr](ksetup-setenctypeattr.md)|Задает один или несколько типов шифрования атрибуты доверия для домена.|
|[ksetup:getenctypeattr](ksetup-getenctypeattr.md)|Возвращает атрибут шифрования типы доверия для домена.|
|[ksetup:addenctypeattr](ksetup-addenctypeattr.md)|Добавляет типы шифрования атрибут шифрования типы доверия для домена.|
|[ksetup:delenctypeattr](ksetup-delenctypeattr.md)|Удаляет атрибут шифрования типы доверия для домена.|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

**Ksetup** используется для изменения параметров компьютера для обнаружения сферы Kerberos. В реализациях под управлением ОС, отличных от Microsoft Kerberos эти сведения обычно сохраняется в файл Krb5.conf. В операционных системах Windows Server он хранится в реестре. Это средство можно использовать для изменения этих параметров. Эти параметры используются, рабочие станции, чтобы найти сфер Kerberos и контроллерами домена, чтобы найти сфер Kerberos для отношения доверия между областями.

**Ksetup** инициализирует раздела реестра для поставщика поддержки безопасности (SSP) Kerberos использует для обнаружения сферы Kerberos KDC, если компьютер под управлением Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2 и не является членом группы Windows домен. После настройки клиентского компьютера под управлением Windows, операционной системы можно выполнить вход на учетные записи пользователей, в области Kerberos.

Протокол Kerberos версии 5 используется по умолчанию для проверки подлинности сети на компьютерах под управлением Windows XP Professional, Windows Vista и Windows 7. Kerberos SSP пытается найти в реестре имя домена сферы пользователя и затем разрешает имя в IP-адресом, запрашивая DNS-сервер. Протокол Kerberos можно использовать DNS для поиска KDC с использованием только имени области, но он должен быть специально настроен для этого.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)