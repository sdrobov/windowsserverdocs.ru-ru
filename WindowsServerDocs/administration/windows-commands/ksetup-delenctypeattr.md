---
title: 'ksetup: деленктипеаттр'
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4fc25ef3-e271-4229-a712-72c507df55aa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2908cc0a095a6985c11f7885766926b7f0354ab0
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724704"
---
# <a name="ksetupdelenctypeattr"></a>ksetup: деленктипеаттр



Удаляет атрибут типа шифрования для домена.

## <a name="syntax"></a>Синтаксис

```
ksetup /delenctypeattr <DomainName> 
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя_домена>|Имя домена, для которого требуется установить соединение. Используйте полное доменное имя или простую форму имени, например corp.contoso.com или contoso.|

## <a name="remarks"></a>Примечания

Чтобы просмотреть тип шифрования билета предоставления билета Kerberos (TGT) и ключа сеанса, выполните команду **klist** и просмотрите выходные данные.

Сообщение о состоянии отображается при успешном или неудачном завершении.

Чтобы задать домен, к которому необходимо подключиться и использовать, выполните команду **ksetup/Domain \<имя_домена>** .

## <a name="examples"></a>Примеры

Определите текущие типы шифрования, установленные на этом компьютере:
```
klist
```
Задайте для домена значение mit.contoso.com:
```
ksetup /domain mit.contoso.com
```
Проверьте атрибут типа шифрования для домена:
```
ksetup /getenctypeattr mit.contoso.com
```
Удалите атрибут SET ENCRYPTION Type для домена mit.contoso.com:
```
ksetup /delenctypeattr mit.contoso.com
```

## <a name="additional-references"></a>Дополнительные ссылки

-   [Klist](klist.md)
-   [Ksetup:domain](ksetup-domain.md)
-   [Ksetup:addenctypeattr](ksetup-addenctypeattr.md)
-   [Ksetup:setenctypeattr](ksetup-setenctypeattr.md)
-   [Ksetup:delenctypeattr](ksetup-delenctypeattr.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)