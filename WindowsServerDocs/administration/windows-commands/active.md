---
title: active
description: Команды Windows для **активных** и базовых дисков помечает раздел фокусом как активный.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f25da2e-87fc-4392-a7ee-f38d09b7873c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c926bf9b7a583cf7eaa23166e09e6f0a1599e625
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382851"
---
# <a name="active"></a>active



На базовых дисках раздел помечается как активный.

> [!CAUTION]
> DiskPart проверяет только то, что Секция может содержать файлы запуска операционной системы. DiskPart не проверяет содержимое раздела. Если вы по ошибке пометите раздел как активный и не содержит загрузочных файлов операционной системы, компьютер может не запуститься.

## <a name="syntax"></a>Синтаксис

```
active
```

## <a name="remarks"></a>Примечания

-   Это информирует основную систему ввода-вывода (BIOS) или интерфейс EFI, что раздел или том является допустимым системным разделом или системным томом.
-   Только секции могут быть помечены как активные.
-   Для выполнения этой операции необходимо выбрать секцию. Используйте команду **Выбор секции** , чтобы выбрать секцию и переместить фокус на нее.

## <a name="BKMK_examples"></a>Примеров

Чтобы пометить секцию фокусом в качестве активной секции, введите:
```
active
```

#### <a name="additional-references"></a>Дополнительная справка

