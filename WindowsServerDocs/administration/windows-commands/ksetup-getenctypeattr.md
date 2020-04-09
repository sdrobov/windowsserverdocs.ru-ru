---
title: 'ksetup: жетенктипеаттр'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6c7ec002-355e-474d-bc27-27215049f1a8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 60de138ac73140c69e9a863083e01a51c0e13ca3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841537"
---
# <a name="ksetupgetenctypeattr"></a>ksetup: жетенктипеаттр



Извлекает атрибут типа шифрования для домена. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /getenctypeattr <DomainName> 
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<имя_домена >|Имя домена, для которого требуется установить соединение. Используйте полное доменное имя или простую форму имени, например corp.contoso.com или contoso.|

## <a name="remarks"></a>Примечания

Чтобы просмотреть тип шифрования билета предоставления билета Kerberos (TGT) и ключа сеанса, выполните команду **klist** и просмотрите выходные данные.

Если команда завершается успешно или неудачно, отображается сообщение о состоянии при успешном или неудачном завершении.

Чтобы задать домен, к которому необходимо подключиться и использовать, выполните команду **ksetup/domain \<имя_домена >** .

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

Проверьте атрибут типа шифрования для домена:
```
ksetup /getenctypeattr mit.contoso.com
```

## <a name="additional-references"></a>Дополнительные материалы

-   [Klist](klist.md)
-   [Ksetup:domain](ksetup-domain.md)
-   [Ksetup:addenctypeattr](ksetup-addenctypeattr.md)
-   [Ksetup:setenctypeattr](ksetup-setenctypeattr.md)
-   [Ksetup:delenctypeattr](ksetup-delenctypeattr.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)