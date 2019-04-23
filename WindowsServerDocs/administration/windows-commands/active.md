---
title: active
description: Раздел Windows команды для **active** — на базовых дисках отмечает раздел как активный.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 3a039e0200fb84d446739ac7017556b6c302f4af
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868765"
---
# <a name="active"></a>active



На базовом диске отмечает раздел как активный.

> [!CAUTION]
> DiskPart проверяет только что раздел может содержать файлы загрузки операционной системы. DiskPart не проверяет содержимое раздела. Если вы по ошибке отметить раздел как активный, и он не содержит файлы загрузки операционной системы, компьютер может не запуститься.

## <a name="syntax"></a>Синтаксис

```
active
```

## <a name="remarks"></a>Примечания

-   Эта информация указывает базовой системы ввода вывода (BIOS) или Extensible Firmware Interface (EFI), что раздел или том является действительным системным разделом или системным томом.
-   Только секции может быть помечен как активный.
-   Для успешного выполнения этой операции необходимо выбрать секцию. Используйте **выберите секцию** команду, чтобы выбрать раздел и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Чтобы отметить раздел как активный раздел, введите следующую команду:
```
active
```

#### <a name="additional-references"></a>Дополнительная справка

