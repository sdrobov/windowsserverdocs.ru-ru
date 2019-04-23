---
title: bitsadmin sethelpertoken
description: Раздел Windows команды для **bitsadmin sethelpertoken** -задает основной маркер текущей командной строке (или токен учетной записи произвольных локального пользователя, если указано) как вспомогательный маркер задание передачи службы BITS.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 558a1aca66a7b3ec447136ceff9237d13efe4ede
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59853005"
---
# <a name="bitsadmin-sethelpertoken"></a>bitsadmin sethelpertoken

Задает основной маркер текущей командной строке (или токен учетной записи произвольных локального пользователя, если указан), как задание передачи службы BITS [вспомогательный маркер](/windows/desktop/bits/helper-tokens-for-bits-transfer-jobs).

**БИТЫ 3.0 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetHelperToken <Job> [\<username@domain\> \<password\>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания.|
|\<username@domain\> \<Пароль\>|Необязательный&mdash;учетные данные локального пользователя учетной записи которого маркер для использования.|

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
