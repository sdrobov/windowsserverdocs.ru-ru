---
title: ksetup
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4e046f8a-811b-48dc-9a69-18d8e097f353
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b3c61fd81691f9db44330eddbf40d4212d1786ff
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841257"
---
# <a name="ksetup"></a>ksetup



Выполняет задачи, связанные с настройкой и обслуживанием протокола Kerberos и центр распространения ключей (KDC) для поддержки сфер Kerberos, которые также не являются доменами Windows. Примеры использования этой команды см. в разделе "примеры" в каждой из связанных подразделов.

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

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[Ksetup:setrealm](ksetup-setrealm.md)|Делает этот компьютер членом области Kerberos.|
|[Ksetup:mapuser](ksetup-mapuser.md)|Сопоставляет субъекта Kerberos с учетной записью.|
|[Ksetup:addkdc](ksetup-addkdc.md)|Определяет запись KDC для данной области.|
|[Ksetup:delkdc](ksetup-delkdc.md)|Удаляет запись KDC для области.|
|[Ksetup:addkpasswd](ksetup-addkpasswd.md)|Добавляет адрес сервера Кпассвд для области.|
|[Ksetup:delkpasswd](ksetup-delkpasswd.md)|Удаляет адрес сервера Кпассвд для области.|
|[Ksetup:server](ksetup-server.md)|Позволяет указать имя компьютера Windows, на котором будут применяться изменения.|
|[Ksetup:setcomputerpassword](ksetup-setcomputerpassword.md)|Задает пароль для учетной записи домена компьютера (или субъекта-узла).|
|[Ksetup:removerealm](ksetup-removerealm.md)|Удаляет из реестра все сведения для указанной области.|
|[Ksetup:domain](ksetup-domain.md)|Позволяет указать домен (если \<имя_домена > не был задан с помощью **/domain**).|
|[Ksetup:changepassword](ksetup-changepassword.md)|Позволяет использовать Кпассвд для изменения пароля пользователя, вошедшего в систему.|
|[Ksetup:listrealmflags](ksetup-listrealmflags.md)|Список доступных флагов области, которые **ksetup** может обнаружить.|
|[Ksetup:setrealmflags](ksetup-setrealmflags.md)|Задает флаги области для определенной области.|
|[Ksetup:addrealmflags](ksetup-addrealmflags.md)|Добавляет дополнительные флаги сферы в область.|
|[Ksetup:delrealmflags](ksetup-delrealmflags.md)|Удаляет флаги сферы из области.|
|[Ksetup:dumpstate](ksetup-dumpstate.md)|Анализирует конфигурацию Kerberos на данном компьютере. Добавляет в реестр сопоставление узла с областью.|
|[Ksetup:addhosttorealmmap](ksetup-addhosttorealmmap.md)|Добавляет значение реестра для отображения узла в области Kerberos.|
|[Ksetup:delhosttorealmmap](ksetup-delhosttorealmmap.md)|Удаляет значение реестра, которое сопоставляет главный компьютер с областью Kerberos.|
|[Ksetup:setenctypeattr](ksetup-setenctypeattr.md)|Задает один или несколько типов шифрования для атрибутов доверия для домена.|
|[Ksetup:getenctypeattr](ksetup-getenctypeattr.md)|Возвращает атрибут доверия типов шифрования для домена.|
|[Ksetup:addenctypeattr](ksetup-addenctypeattr.md)|Добавляет типы шифрования в атрибут Trust типов шифрования для домена.|
|[Ksetup:delenctypeattr](ksetup-delenctypeattr.md)|Удаляет атрибут доверия типов шифрования для домена.|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

**Ksetup** используется для изменения параметров компьютера для обнаружения сфер Kerberos. В реализациях, отличных от Microsoft Kerberos, эта информация обычно хранится в файле krb5. conf. В операционных системах Windows Server она хранится в реестре. Это средство можно использовать для изменения этих параметров. Эти параметры используются рабочими станциями для нахождение сфер Kerberos и контроллеров домена для нахождение сфер Kerberos для отношений доверия между сферами.

**Ksetup** инициализирует разделы реестра, используемые поставщиком службы поддержки безопасности Kerberos (SSP) для определения местонахождения центра распространения ключей для области Kerberos, если компьютер работает под windows Server 2003, windows Server 2008 или windows Server 2008 R2 и не является членом домена Windows. После настройки пользователь клиентского компьютера, работающего под управлением операционной системы Windows, может войти в учетные записи в области Kerberos.

Протокол Kerberos версии 5 используется по умолчанию для проверки подлинности сети на компьютерах под управлением Windows XP Professional, Windows Vista и Windows 7. ПОСТАВЩИК удостоверений Kerberos ищет в реестре доменное имя области пользователя, а затем разрешает имя в IP-адрес, запрашивая DNS-сервер. Протокол Kerberos может использовать DNS для определения Кдкс только с именем области, но для этого он должен быть специально настроен.

## <a name="additional-references"></a>Дополнительные материалы

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)