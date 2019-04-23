---
title: ksetup:domain
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 1f53e807891b434709b1a8faed7aae8e8d444f6e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59857455"
---
# <a name="ksetupdomain"></a>ksetup:domain



Задает имя домена для всех операций Kerberos. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /domain <DomainName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя домена >|Имя домена, к которому вы хотите установить соединение. Используйте полное доменное имя или простую форму имени, например contoso.com или contoso.|

## <a name="remarks"></a>Примечания

Нет.

## <a name="BKMK_Examples"></a>Примеры

Установите подключение к допустимый домен, например Microsoft с помощью подкоманды /mapuser:
```
ksetup /mapuser principal@realm domain-user /domain domain-name
```
Если подключение установлено успешно, вы получите новый TGT или существующих TGT будет обновлен.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)