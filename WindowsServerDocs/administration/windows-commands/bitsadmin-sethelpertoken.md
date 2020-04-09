---
title: битсадмин сеселпертокен
description: Раздел команд Windows для битсадмин сеселпертокен, который задает основной маркер текущей командной строки (или маркер произвольной учетной записи локального пользователя, если он указан) в качестве вспомогательного токена задания передачи BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: a1e8fd0054cadf3bf06b6e5b7bdf5010b18781e1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849537"
---
# <a name="bitsadmin-sethelpertoken"></a>битсадмин сеселпертокен

Задает основной маркер текущей командной строки (или маркер произвольной учетной записи локального пользователя, если он указан) в качестве [вспомогательного токена](/windows/desktop/bits/helper-tokens-for-bits-transfer-jobs)задания передачи BITS.

**BITS 3,0 и более ранних версий**: не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetHelperToken <Job> [\<username@domain\> \<password\>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID.|
|\<username@domain\> \<пароль\>|Необязательно&mdash;учетные данные локальной учетной записи пользователя, токен которой будет использоваться.|

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
