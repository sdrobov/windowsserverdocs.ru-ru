---
title: 'ksetup: сетенктипеаттр'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88fb913e-6b57-48d9-8c16-a035ab2977ac
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bcc268ecb591e3008d7274f6c9f6d6017c86f99d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374930"
---
# <a name="ksetupsetenctypeattr"></a>ksetup: сетенктипеаттр



Задает атрибут типа шифрования для домена. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /setenctypeattr <Domain name> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0DomainName >|Имя домена, для которого требуется установить соединение. Используйте полное доменное имя или простую форму имени, например corp.contoso.com или contoso.|
|Тип шифрования|Должен быть одним из следующих поддерживаемых типов шифрования:</br>-DES-CBC-CRC</br>-DES-CBC-MD5</br>-RC4-HMAC-MD5</br>-AES128-CTS-HMAC-SHA1-96</br>-AES256-CTS-HMAC-SHA1-96|

## <a name="remarks"></a>Примечания

Чтобы просмотреть тип шифрования билета предоставления билета Kerberos (TGT) и ключа сеанса, выполните команду **klist** и просмотрите выходные данные.

Можно задать или добавить несколько типов шифрования, разделяя типы шифрования в команде пробелами. Однако это можно сделать только для одного домена за раз.

Если команда завершается успешно или неудачно, отображается сообщение о состоянии.

Чтобы задать домен, к которому необходимо подключиться и использовать, выполните команду **ksetup/domain \<DomainName >** .

## <a name="BKMK_Examples"></a>Примеров

Определите текущие типы шифрования, установленные на этом компьютере:
```
klist
```
Задайте для домена значение corp.contoso.com:
```
ksetup /domain corp.contoso.com
```
Задайте для атрибута типа шифрования значение AES-256-CTS-HMAC-SHA1-96 для домена corp.contoso.com:
```
ksetup /setenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```
Убедитесь, что атрибут типа шифрования был установлен в соответствии с целью домена:
```
ksetup /getenctypeattr corp.contoso.com
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Klist](klist.md)
-   [Ksetup:domain](ksetup-domain.md)
-   [Ksetup:addenctypeattr](ksetup-addenctypeattr.md)
-   [Ksetup:getenctypeattr](ksetup-getenctypeattr.md)
-   [Ksetup:delenctypeattr](ksetup-delenctypeattr.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)