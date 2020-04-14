---
title: Размер BdeHdCfg
description: Раздел команд Windows для **BdeHdCfg size**, который указывает размер системного раздела при создании нового системного диска.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 80f55b1d-a28d-4edf-9997-1fb918b7b5a1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c72bdfd0b8bf4dfd0aa36885ceb7fd249a18c332
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851027"
---
# <a name="bdehdcfg-size"></a>BdeHdCfg: размер

Указывает размер системного раздела при создании нового системного диска.

Пример того, как можно использовать эту команду, см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink} -size <SizeinMB>
```

#### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<SizeinMB>` | Указывает количество мегабайтов (МБ), используемых для новой секции. |

## <a name="remarks"></a>Примечания

Если размер не указан, средство будет использовать значение по умолчанию 300 МБ. Минимальный размер системного диска составляет 100 МБ. Если вы будете хранить в системном разделе Восстановление системы или другие системные средства, следует соответственно увеличить размер.

> [!NOTE]
> Команду **size** нельзя сочетать с **целевой** командой `<DriveLetter>` **Merge** .

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

В следующем примере показано использование команды **size** для выделения 500 МБ на системном диске по умолчанию.

```
bdehdcfg -target default -size 500
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [BdeHdCfg](bdehdcfg.md)