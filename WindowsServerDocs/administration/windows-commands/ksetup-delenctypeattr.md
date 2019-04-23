---
title: ksetup:delenctypeattr
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 9c2cc96e8156cafd3846422596abe62513e275b3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59838135"
---
# <a name="ksetupdelenctypeattr"></a>ksetup:delenctypeattr



Удаляет атрибут типа шифрования для домена. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /delenctypeattr <DomainName> 
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя домена >|Имя домена, к которому вы хотите установить соединение. Используйте полное доменное имя или простую форму имени, например corp.contoso.com или contoso.|

## <a name="remarks"></a>Примечания

Чтобы просмотреть тип шифрования для Kerberos билет предоставления билета (TGT) и ключ сеанса, выполните **klist** команды и просмотреть выходные данные.

После завершения успешной или неуспешной отображается сообщение о состоянии.

Чтобы задать домен, который необходимо для подключения и использования, выполните **/Domain ksetup \<DomainName >** команды.

## <a name="BKMK_Examples"></a>Примеры

Определите текущие типы шифрования, установленных на этом компьютере:
```
klist
```
Задайте домен mit.contoso.com:
```
ksetup /domain mit.contoso.com
```
Убедитесь, что атрибут типа шифрования для домена.
```
ksetup /getenctypeattr mit.contoso.com
```
Удалите атрибут типа набора шифрования для mit.contoso.com домена:
```
ksetup /delenctypeattr mit.contoso.com
```

#### <a name="additional-references"></a>Дополнительная справка

-   [klist](klist.md)
-   [ksetup:domain](ksetup-domain.md)
-   [ksetup:addenctypeattr](ksetup-addenctypeattr.md)
-   [ksetup:setenctypeattr](ksetup-setenctypeattr.md)
-   [ksetup:delenctypeattr](ksetup-delenctypeattr.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)