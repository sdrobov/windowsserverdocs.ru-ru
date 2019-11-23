---
title: битсадмин сеселпертокен
description: Раздел команд Windows для **битсадмин сеселпертокен** . задает основной маркер текущей командной строки (или маркер произвольной учетной записи локального пользователя, если он указан) в качестве вспомогательного токена задания передачи BITS.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 91c03366998168dad9ab4530ef36a5020b8ad6ec
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380570"
---
# <a name="bitsadmin-sethelpertoken"></a>битсадмин сеселпертокен

Задает основной маркер текущей командной строки (или маркер произвольной учетной записи локального пользователя, если он указан) в качестве [вспомогательного токена](/windows/desktop/bits/helper-tokens-for-bits-transfer-jobs)задания передачи BITS.

**BITS 3,0 и более ранних версий**: не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetHelperToken <Job> [\<username@domain\> \<password\>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID.|
|\<username@domain\> \<пароль\>|Необязательно&mdash;учетные данные локальной учетной записи пользователя, токен которой будет использоваться.|

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
