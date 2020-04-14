---
title: select
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9eeb40c0-4258-46e2-8dbc-94f63497e771
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f9ad7051978f4b509f54bf783f71943b65617bc7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834657"
---
# <a name="select"></a>select



Перемещает фокус на диск, раздел, том или виртуальный жесткий диск (VHD).

## <a name="syntax"></a>Синтаксис

```
select disk
select partition
select volume
select vdisk
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[Выбор диска](select-disk.md)|Перемещает фокус на диск.|
|[Выбор Секции](select-partition.md)|Сдвигает фокус на секцию.|
|[Выбор тома](select-volume.md)|Перемещает фокус на том.|
|[Выбрать виртуальный диск](select-vdisk.md)|Перемещает фокус на виртуальный жесткий диск.|

## <a name="remarks"></a>Примечания

-   Если выбран том с соответствующим разделом, раздел будет выбран автоматически.
-   Если секция выбрана с соответствующим томом, том будет выбран автоматически.

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

