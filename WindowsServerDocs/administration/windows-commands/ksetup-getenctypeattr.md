---
title: 'ksetup: жетенктипеаттр'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6c7ec002-355e-474d-bc27-27215049f1a8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1ff55cfd204f76b42c5f1342b3cf206ee4c14f14
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374992"
---
# <a name="ksetupgetenctypeattr"></a>ksetup: жетенктипеаттр



Извлекает атрибут типа шифрования для домена. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /getenctypeattr <DomainName> 
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0DomainName >|Имя домена, для которого требуется установить соединение. Используйте полное доменное имя или простую форму имени, например corp.contoso.com или contoso.|

## <a name="remarks"></a>Примечания

Чтобы просмотреть тип шифрования билета предоставления билета Kerberos (TGT) и ключа сеанса, выполните команду **klist** и просмотрите выходные данные.

Если команда завершается успешно или неудачно, отображается сообщение о состоянии при успешном или неудачном завершении.

Чтобы задать домен, к которому необходимо подключиться и использовать, выполните команду **ksetup/domain \<DomainName >** .

## <a name="BKMK_Examples"></a>Примеров

Проверьте атрибут типа шифрования для домена:
```
ksetup /getenctypeattr mit.contoso.com
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Klist](klist.md)
-   [Ksetup:domain](ksetup-domain.md)
-   [Ksetup:addenctypeattr](ksetup-addenctypeattr.md)
-   [Ksetup:setenctypeattr](ksetup-setenctypeattr.md)
-   [Ksetup:delenctypeattr](ksetup-delenctypeattr.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)