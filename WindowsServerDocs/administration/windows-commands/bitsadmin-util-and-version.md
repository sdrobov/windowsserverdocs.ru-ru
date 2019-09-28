---
title: битсадмин util и версия
description: Раздел команд Windows для **битсадмин util и Version** — отображает версию службы BITS.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98f17328-dfbd-4cbb-93c1-b8d424bc3f0a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 495ef17bbf6f39f20f6729b64de4b4bec0f9a3c2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380197"
---
# <a name="bitsadmin-util-and-version"></a>битсадмин util и версия

Отображает версию службы BITS (например, 2,0).

**Битсадмин 1,5 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Util /Version [/Verbose]
```

## <a name="remarks"></a>Примечания

Параметр **verbose** выполняет следующие действия:
-   Отображает версию файла для каждой библиотеки DLL, связанной с BITS
-   Проверяет, можно ли запустить службу BITS
-   Отображение значений групповая политика BITS (только для Windows Vista)

## <a name="BKMK_examples"></a>Примеров

В следующем примере показана версия службы BITS.
```
C:\>bitsadmin /Util /Version
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)