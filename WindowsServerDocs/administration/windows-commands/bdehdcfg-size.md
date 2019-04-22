---
title: размер bdehdcfg
description: Раздел Windows команды — размер системного раздела при создании нового диска системы.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80f55b1d-a28d-4edf-9997-1fb918b7b5a1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d024bb4092f93782300d6afb9053cee1da32629a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817525"
---
# <a name="bdehdcfg-size"></a>bdehdcfg: размер



Указывает размер системного раздела, при создании нового диска системы. Пример того, как эту команду можно использовать, см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink} -size <SizeinMB>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<SizeinMB>|Указывает размер в мегабайтах (МБ), чтобы использовать для новой секции.|

## <a name="remarks"></a>Примечания

Если размер не задан, средство будет использовать значение по умолчанию 300 МБ. Минимальный размер системного диска составляет 100 МБ. Если вы хотите сохранить восстановление системы или других системных средств в системном разделе, следует увеличить размер соответствующим образом.

> [!NOTE]
> **Размер** команду нельзя использовать вместе с **целевой** \<буква_диска > **слияния** команды.

## <a name="BKMK_Examples"></a>Примеры

В следующем примере демонстрируется использование **размер** команду, чтобы выделить 500 МБ для системного диска по умолчанию.
```
bdehdcfg -target default -size 500
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Bdehdcfg](bdehdcfg.md)