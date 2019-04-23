---
title: bitsadmin util и версии
description: Раздел Windows команды для **bitsadmin util и версии** -отображает версию службы BITS.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 2e768ec5ae43fc17c480b9deede698cca01c6291
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882875"
---
# <a name="bitsadmin-util-and-version"></a>bitsadmin util и версии

Отображает версию службы BITS (например, 2.0).

**BITSAdmin 1.5 и более ранних**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Util /Version [/Verbose]
```

## <a name="remarks"></a>Примечания

**Verbose** параметр выполняет следующее:
-   Отображает версию файла для каждой библиотеки DLL соответствующим BITS
-   Подтверждает, что запускается служба BITS
-   Отображает значения БИТОВ групповой политики (только для Windows Vista)

## <a name="BKMK_examples"></a>Примеры

Ниже приведен пример версию службы BITS.
```
C:\>bitsadmin /Util /Version
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)