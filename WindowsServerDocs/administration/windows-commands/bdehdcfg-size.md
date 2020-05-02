---
title: Размер BdeHdCfg
description: Справочный раздел по команде размера BdeHdCfg, который указывает размер системного раздела при создании нового системного диска.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 80f55b1d-a28d-4edf-9997-1fb918b7b5a1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 27662a46045a8701b40697198cddf1dcb1b51c1e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718613"
---
# <a name="bdehdcfg-size"></a>BdeHdCfg: размер

Указывает размер системного раздела при создании нового системного диска. Если размер не указан, средство будет использовать значение по умолчанию 300 МБ. Минимальный размер системного диска составляет 100 МБ. Если вы будете хранить в системном разделе Восстановление системы или другие системные средства, следует соответственно увеличить размер.

> [!NOTE]
> Команда **size** не может быть объединена с `target <drive_letter> merge` командой.

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink} -size <size_in_mb>
```

#### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<size_in_mb>` | Указывает количество мегабайтов (МБ), используемых для новой секции. |

## <a name="examples"></a>Примеры

Чтобы выделить 500 МБ на системный диск по умолчанию:

```
bdehdcfg -target default -size 500
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
