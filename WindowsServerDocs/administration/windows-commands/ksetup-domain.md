---
title: 'ksetup: домен'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2ef766e3-6071-44f2-946b-22ea5b61a508
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0a4d9f09def32c7518046c25887f4154020c5d7e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375124"
---
# <a name="ksetupdomain"></a>ksetup: домен



Задает доменное имя для всех операций Kerberos. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /domain <DomainName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0DomainName >|Имя домена, для которого требуется установить соединение. Используйте полное доменное имя или простую форму имени, например contoso.com или contoso.|

## <a name="remarks"></a>Примечания

Нет.

## <a name="BKMK_Examples"></a>Примеров

Установите подключение к допустимому домену, например Microsoft, с помощью подкоманды/мапусер:
```
ksetup /mapuser principal@realm domain-user /domain domain-name
```
После успешного подключения вы получите новый TGT или обновите существующий TGT.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)