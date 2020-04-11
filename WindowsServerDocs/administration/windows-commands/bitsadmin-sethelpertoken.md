---
title: битсадмин сеселпертокен
description: Раздел команд Windows для **битсадмин сеселпертокен**, который задает основной маркер текущей командной строки (или маркер произвольной учетной записи локального пользователя, если он указан) в качестве вспомогательного токена задания передачи BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: ba4b9a4ed1b59d1b1aeda30353317739b7fdfa9e
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122984"
---
# <a name="bitsadmin-sethelpertoken"></a>битсадмин сеселпертокен

Задает основной маркер текущей командной строки (или маркер произвольной учетной записи локального пользователя, если он указан) в качестве [вспомогательного токена](https://docs.microsoft.com/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)задания передачи BITS.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 3,0 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /sethelpertoken <job> [<user_name@domain> <password>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| `<username@domain>` `<password>` | Необязательно. Учетные данные локального пользователя, для которых используется токен. |

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
