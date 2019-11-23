---
title: 'ksetup: деленктипеаттр'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4fc25ef3-e271-4229-a712-72c507df55aa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e3810d83c06b9ea08766451e13390b02b1867c83
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375157"
---
# <a name="ksetupdelenctypeattr"></a>ksetup: деленктипеаттр



Удаляет атрибут типа шифрования для домена. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /delenctypeattr <DomainName> 
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<имя_домена >|Имя домена, для которого требуется установить соединение. Используйте полное доменное имя или простую форму имени, например corp.contoso.com или contoso.|

## <a name="remarks"></a>Замечания

Чтобы просмотреть тип шифрования билета предоставления билета Kerberos (TGT) и ключа сеанса, выполните команду **klist** и просмотрите выходные данные.

Сообщение о состоянии отображается при успешном или неудачном завершении.

Чтобы задать домен, к которому необходимо подключиться и использовать, выполните команду **ksetup/domain \<имя_домена >** .

## <a name="BKMK_Examples"></a>Примеров

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

#### <a name="additional-references"></a>Дополнительная справка

-   [Klist](klist.md)
-   [Ksetup:domain](ksetup-domain.md)
-   [Ksetup:addenctypeattr](ksetup-addenctypeattr.md)
-   [Ksetup:setenctypeattr](ksetup-setenctypeattr.md)
-   [Ksetup:delenctypeattr](ksetup-delenctypeattr.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)