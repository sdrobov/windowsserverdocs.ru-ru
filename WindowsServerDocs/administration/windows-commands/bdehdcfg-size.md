---
title: Размер BdeHdCfg
description: Раздел команд Windows — указывает размер системного раздела при создании нового системного диска.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 6ec42cdb5716c63c7210ea6cfde8ce8884833b45
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382201"
---
# <a name="bdehdcfg-size"></a>BdeHdCfg: размер



Указывает размер системного раздела при создании нового системного диска. Пример того, как можно использовать эту команду, см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink} -size <SizeinMB>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0SizeinMB >|Указывает количество мегабайтов (МБ), используемых для новой секции.|

## <a name="remarks"></a>Примечания

Если размер не указан, средство будет использовать значение по умолчанию 300 МБ. Минимальный размер системного диска составляет 100 МБ. Если вы будете хранить в системном разделе Восстановление системы или другие системные средства, следует соответственно увеличить размер.

> [!NOTE]
> Команду **size** нельзя сочетать с **целевой** командой \<DriveLetter > **Merge** .

## <a name="BKMK_Examples"></a>Примеров

В следующем примере показано использование команды **size** для выделения 500 МБ на системном диске по умолчанию.
```
bdehdcfg -target default -size 500
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [BdeHdCfg](bdehdcfg.md)