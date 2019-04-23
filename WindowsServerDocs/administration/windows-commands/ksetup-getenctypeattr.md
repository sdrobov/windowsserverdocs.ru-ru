---
title: ksetup:getenctypeattr
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 302f94616f98eb350332b08ad37a58305a0a0be1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59841995"
---
# <a name="ksetupgetenctypeattr"></a>ksetup:getenctypeattr



Получает атрибут типа шифрования для домена. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /getenctypeattr <DomainName> 
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя домена >|Имя домена, к которому вы хотите установить соединение. Используйте полное доменное имя или простую форму имени, например corp.contoso.com или contoso.|

## <a name="remarks"></a>Примечания

Чтобы просмотреть тип шифрования для Kerberos билет предоставления билета (TGT) и ключ сеанса, выполните **klist** команды и просмотреть выходные данные.

Если команда успешного или неуспешного выполнения, после завершения успешной или неуспешной отображается сообщение о состоянии.

Чтобы задать домен, который необходимо для подключения и использования, выполните **/Domain ksetup \<DomainName >** команды.

## <a name="BKMK_Examples"></a>Примеры

Проверьте атрибут типа шифрования для домена:
```
ksetup /getenctypeattr mit.contoso.com
```

#### <a name="additional-references"></a>Дополнительная справка

-   [klist](klist.md)
-   [ksetup:domain](ksetup-domain.md)
-   [ksetup:addenctypeattr](ksetup-addenctypeattr.md)
-   [ksetup:setenctypeattr](ksetup-setenctypeattr.md)
-   [ksetup:delenctypeattr](ksetup-delenctypeattr.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)