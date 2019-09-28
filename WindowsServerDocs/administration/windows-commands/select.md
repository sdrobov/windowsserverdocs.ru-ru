---
title: отключения
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9eeb40c0-4258-46e2-8dbc-94f63497e771
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7dc3bc8775f971968f096ba4344348e77c112cfa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384108"
---
# <a name="select"></a>отключения



Перемещает фокус на диск, раздел, том или виртуальный жесткий диск (VHD).

## <a name="syntax"></a>Синтаксис

```
select disk
select partition
select volume
select vdisk
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[Выбор диска](select-disk.md)|Перемещает фокус на диск.|
|[Выбор Секции](select-partition.md)|Сдвигает фокус на секцию.|
|[Выбор тома](select-volume.md)|Перемещает фокус на том.|
|[Выбрать виртуальный диск](select-vdisk.md)|Перемещает фокус на виртуальный жесткий диск.|

## <a name="remarks"></a>Примечания

-   Если выбран том с соответствующим разделом, раздел будет выбран автоматически.
-   Если секция выбрана с соответствующим томом, том будет выбран автоматически.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

