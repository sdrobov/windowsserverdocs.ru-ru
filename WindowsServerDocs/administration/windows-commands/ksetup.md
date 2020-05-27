---
title: ksetup
description: Справочный раздел по команде ksetup, который выполняет задачи, связанные с настройкой и обслуживанием протокола Kerberos и центр распространения ключей (KDC) для поддержки сфер Kerberos.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4e046f8a-811b-48dc-9a69-18d8e097f353
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 82b1627a8ddbc9e51ac32825c5a42c3df9effbf7
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817354"
---
# <a name="ksetup"></a>ksetup

Выполняет задачи, связанные с настройкой и обслуживанием протокола Kerberos и центр распространения ключей (KDC) для поддержки сфер Kerberos. В частности, эта команда используется в следующих случаях:

- Измените параметры компьютера для обнаружения сфер Kerberos. В реализациях, основанных не на базе протокола Kerberos, эта информация обычно хранится в файле krb5. conf. В операционных системах Windows Server она хранится в реестре. Это средство можно использовать для изменения этих параметров. Эти параметры используются рабочими станциями для нахождение сфер Kerberos и контроллеров домена для нахождение сфер Kerberos для отношений доверия между сферами.

- Инициализируйте разделы реестра, используемые поставщиком поддержки безопасности Kerberos (SSP) для определения местонахождения центра распространения ключей для области Kerberos, если компьютер не является членом домена Windows. После настройки пользователь клиентского компьютера под управлением операционной системы Windows может войти в учетную запись в области Kerberos.

- Найдите в реестре доменное имя области пользователя, а затем разрешите имя по IP-адресу, запросив DNS-сервер. Протокол Kerberos может использовать DNS для определения Кдкс только с именем области, но для этого он должен быть специально настроен.

## <a name="syntax"></a>Синтаксис

```
ksetup
[/setrealm <DNSdomainname>]
[/mapuser <principal> <account>]
[/addkdc <realmname> <KDCname>]
[/delkdc <realmname> <KDCname>]
[/addkpasswd <realmname> <KDCPasswordName>]
[/delkpasswd <realmname> <KDCPasswordName>]
[/server <servername>]
[/setcomputerpassword <password>]
[/removerealm <realmname>]
[/domain <domainname>]
[/changepassword <oldpassword> <newpassword>]
[/listrealmflags]
[/setrealmflags <realmname> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]]
[/addrealmflags <realmname> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]]
[/delrealmflags [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]]
[/dumpstate]
[/addhosttorealmmap] <hostname> <realmname>]
[/delhosttorealmmap] <hostname> <realmname>]
[/setenctypeattr] <domainname> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
[/getenctypeattr] <domainname>
[/addenctypeattr] <domainname> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
[/delenctypeattr] <domainname>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| [ksetup сетреалм](ksetup-setrealm.md) | Делает этот компьютер членом области Kerberos. |
| [ksetup аддкдк](ksetup-addkdc.md) | Определяет запись KDC для данной области. |
| [ksetup делкдк](ksetup-delkdc.md) | Удаляет запись KDC для области. |
| [ksetup аддкпассвд](ksetup-addkpasswd.md) | Добавляет адрес сервера кпассвд для области. |
| [ksetup делкпассвд](ksetup-delkpasswd.md) | Удаляет адрес сервера кпассвд для области. |
| [сервер ksetup](ksetup-server.md) | Позволяет указать имя компьютера Windows, на котором будут применяться изменения. |
| [ksetup сеткомпутерпассворд](ksetup-setcomputerpassword.md) | Задает пароль для учетной записи домена компьютера (или субъекта-узла). |
| [ksetup ремовереалм](ksetup-removerealm.md) | Удаляет из реестра все сведения для указанной области. |
| [домен ksetup](ksetup-domain.md) | Позволяет указать домен (если он еще `<domainname>` не был задан параметром **/domain** ). |
| [ksetup ChangePassword](ksetup-changepassword.md) | Позволяет использовать кпассвд для изменения пароля пользователя, вошедшего в систему. |
| [ksetup листреалмфлагс](ksetup-listrealmflags.md) | Список доступных флагов области, которые **ksetup** может обнаружить. |
| [ksetup сетреалмфлагс](ksetup-setrealmflags.md) | Задает флаги области для определенной области. |
| [ksetup аддреалмфлагс](ksetup-addrealmflags.md) | Добавляет дополнительные флаги сферы в область. |
| [ksetup делреалмфлагс](ksetup-delrealmflags.md) | Удаляет флаги сферы из области. |
| [ksetup думпстате](ksetup-dumpstate.md) | Анализирует конфигурацию Kerberos на данном компьютере. Добавляет в реестр сопоставление узла с областью. |
| [ksetup аддхосттореалммап](ksetup-addhosttorealmmap.md) | Добавляет значение реестра для отображения узла в области Kerberos. |
| [ksetup делхосттореалммап](ksetup-delhosttorealmmap.md) | Удаляет значение реестра, которое сопоставляет главный компьютер с областью Kerberos. |
| [ksetup сетенктипеаттр](ksetup-setenctypeattr.md) | Задает один или несколько типов шифрования для атрибутов доверия для домена. |
| [ksetup жетенктипеаттр](ksetup-getenctypeattr.md) | Возвращает атрибут доверия типов шифрования для домена. |
| [ksetup адденктипеаттр](ksetup-addenctypeattr.md) | Добавляет типы шифрования в атрибут Trust типов шифрования для домена. |
| [ksetup деленктипеаттр](ksetup-delenctypeattr.md) | Удаляет атрибут доверия типов шифрования для домена. |
| /? | Отображает справку в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)