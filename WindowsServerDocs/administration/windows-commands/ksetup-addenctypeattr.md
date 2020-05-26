---
title: ksetup адденктипеаттр
description: Справочный раздел по команде ksetup адденктипеаттр, который добавляет атрибут типа шифрования в список возможных типов для домена.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 32cc87d7-b9e1-4d14-9eb7-3b439c55aa3a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b7162e35c88cea0cfa2828e12cc4af59eaed66c9
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83818154"
---
# <a name="ksetup-addenctypeattr"></a>ksetup адденктипеаттр

Добавляет атрибут типа шифрования в список возможных типов для домена. Сообщение о состоянии отображается при успешном или неудачном завершении.

## <a name="syntax"></a>Синтаксис

```
ksetup /addenctypeattr <domainname> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<domainname>` | Имя домена, для которого требуется установить соединение. Используйте полное доменное имя или простую форму имени, например corp.contoso.com или contoso. |
| тип шифрования | Должен быть одним из следующих поддерживаемых типов шифрования:<ul><li>DES-CBC-CRC</li><li>DES-CBC-MD5</li><li>RC4-HMAC-MD5</li><li>AES128-CTS-HMAC-SHA1-96</li><li>AES256-CTS-HMAC-SHA1-96</li></ul> |

#### <a name="remarks"></a>Замечания

- Можно задать или добавить несколько типов шифрования, разделяя типы шифрования в команде пробелами. Однако это можно сделать только для одного домена за раз.

### <a name="examples"></a>Примеры

Чтобы просмотреть тип шифрования билета предоставления билета Kerberos (TGT) и ключа сеанса, введите:

```
klist
```

Чтобы задать для домена значение corp.contoso.com, введите:

```
ksetup /domain corp.contoso.com
```

Чтобы добавить тип шифрования *AES-256-CTS-HMAC-SHA1-96* в список возможных типов для домена *Corp.contoso.com*, введите:

```
ksetup /addenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```

Чтобы задать для атрибута типа шифрования значение *AES-256-CTS-HMAC-SHA1-96* для домена *Corp.contoso.com*, введите:

```
ksetup /setenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```

Чтобы убедиться, что атрибут типа шифрования был задан в качестве назначения для домена, введите:

```
ksetup /getenctypeattr corp.contoso.com
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда klist](klist.md)

- [Команда ksetup](ksetup.md)

- [Команда домена ksetup](ksetup-domain.md)

- [ksetup сетенктипеаттр, команда](ksetup-setenctypeattr.md)

- [ksetup жетенктипеаттр, команда](ksetup-getenctypeattr.md)

- [ksetup деленктипеаттр, команда](ksetup-delenctypeattr.md)
