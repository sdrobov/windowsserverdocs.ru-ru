---
title: ksetup:addenctypeattr
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32cc87d7-b9e1-4d14-9eb7-3b439c55aa3a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 711da6a81269fc838ca091765ddbcac63c3fe6e4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59886395"
---
# <a name="ksetupaddenctypeattr"></a>ksetup:addenctypeattr



Добавляет атрибут типа шифрования в список возможных типов для домена. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addenctypeattr <DomainName> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя домена >|Имя домена, к которому вы хотите установить соединение. Используйте полное доменное имя или простую форму имени, например corp.contoso.com или contoso.|
|Тип шифрования|Необходимо принимать следующие поддерживаемые типы шифрования:</br>-   DES-CBC-CRC</br>-   DES-CBC-MD5</br>-   RC4-HMAC-MD5</br>-   AES128-CTS-HMAC-SHA1-96</br>-   AES256-CTS-HMAC-SHA1-96|

## <a name="remarks"></a>Примечания

Чтобы просмотреть тип шифрования для Kerberos билет предоставления билета (TGT) и ключ сеанса, выполните **klist** команды и просмотреть выходные данные.

Можно задать или добавить несколько типов шифрования, разделив типов шифрования в команде с пробелом. Тем не менее вы можете делать только для одного домена за раз.

Если команда успешного или неуспешного выполнения, отображается сообщение о состоянии.

Чтобы задать домен, который необходимо для подключения и использования, выполните **/Domain ksetup \<DomainName >** команды.

## <a name="BKMK_Examples"></a>Примеры

Определите текущие типы шифрования, установленных на этом компьютере:
```
klist
```
Задайте для домена corp.contoso.com.
```
ksetup /domain corp.contoso.com
```
Добавьте тип шифрования AES-256-CTS-HMAC-SHA1-96 список возможных типов для домена corp.contoso.com:
```
ksetup /addenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```
Атрибут типа шифрования, задайте для AES-256-CTS-HMAC-SHA1-96 для домена corp.contoso.com:
```
ksetup /setenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```
Убедитесь, что атрибут типа шифрования был так, как предполагалось, для домена:
```
ksetup /getenctypeattr corp.contoso.com
```

#### <a name="additional-references"></a>Дополнительная справка

-   [klist](klist.md)
-   [ksetup:domain](ksetup-domain.md)
-   [ksetup:setenctypeattr](ksetup-setenctypeattr.md)
-   [ksetup:getenctypeattr](ksetup-getenctypeattr.md)
-   [ksetup:delenctypeattr](ksetup-delenctypeattr.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)