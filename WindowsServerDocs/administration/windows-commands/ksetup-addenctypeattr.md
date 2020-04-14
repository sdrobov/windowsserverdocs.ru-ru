---
title: 'ksetup: адденктипеаттр'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 32cc87d7-b9e1-4d14-9eb7-3b439c55aa3a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 217e8a707c0af23901da3f433f630b253360f093
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841947"
---
# <a name="ksetupaddenctypeattr"></a>ksetup: адденктипеаттр



Добавляет атрибут типа шифрования в список возможных типов для домена. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addenctypeattr <DomainName> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<имя_домена >|Имя домена, для которого требуется установить соединение. Используйте полное доменное имя или простую форму имени, например corp.contoso.com или contoso.|
|Тип шифрования|Должен быть одним из следующих поддерживаемых типов шифрования:</br>-DES-CBC-CRC</br>-DES-CBC-MD5</br>-RC4-HMAC-MD5</br>-AES128-CTS-HMAC-SHA1-96</br>-AES256-CTS-HMAC-SHA1-96|

## <a name="remarks"></a>Примечания

Чтобы просмотреть тип шифрования билета предоставления билета Kerberos (TGT) и ключа сеанса, выполните команду **klist** и просмотрите выходные данные.

Можно задать или добавить несколько типов шифрования, разделяя типы шифрования в команде пробелами. Однако это можно сделать только для одного домена за раз.

Если команда завершается успешно или неудачно, отображается сообщение о состоянии.

Чтобы задать домен, к которому необходимо подключиться и использовать, выполните команду **ksetup/domain \<имя_домена >** .

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

Определите текущие типы шифрования, установленные на этом компьютере:
```
klist
```
Задайте для домена значение corp.contoso.com:
```
ksetup /domain corp.contoso.com
```
Добавьте тип шифрования AES-256-CTS-HMAC-SHA1-96 в список возможных типов для домена corp.contoso.com:
```
ksetup /addenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```
Задайте для атрибута типа шифрования значение AES-256-CTS-HMAC-SHA1-96 для домена corp.contoso.com:
```
ksetup /setenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```
Убедитесь, что атрибут типа шифрования был установлен в соответствии с целью домена:
```
ksetup /getenctypeattr corp.contoso.com
```

## <a name="additional-references"></a>Дополнительные материалы

-   [Klist](klist.md)
-   [Ksetup:domain](ksetup-domain.md)
-   [Ksetup:setenctypeattr](ksetup-setenctypeattr.md)
-   [Ksetup:getenctypeattr](ksetup-getenctypeattr.md)
-   [Ksetup:delenctypeattr](ksetup-delenctypeattr.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)