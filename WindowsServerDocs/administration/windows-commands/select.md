---
title: отключения
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 4c3723dd414adca68c22011ef3f6be02eb6531d5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889905"
---
# <a name="select"></a>отключения



Перемещение фокуса на диске, секции, тома или виртуального жесткого диска (VHD).

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
|[Выберите диск](select-disk.md)|Перемещение фокуса на диск.|
|[Выберите секцию](select-partition.md)|Перемещение фокуса на секции.|
|[Выберите том](select-volume.md)|Перемещение фокуса на томе.|
|[Выберите виртуальный диск](select-vdisk.md)|Перемещение фокуса к виртуальному жесткому диску.|

## <a name="remarks"></a>Примечания

-   Если том с соответствующей секции, секции выбирается автоматически.
-   Если выбрана секция с соответствующим томом, том будет определяться автоматически.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

