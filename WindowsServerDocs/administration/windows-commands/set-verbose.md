---
title: Задать verbose
description: Справочный раздел по параметру SET Verbose, который указывает, следует ли предоставлять подробный вывод при создании теневой копии.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 93cb93c9-666f-4c74-814b-1c404a949935
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: db31192037e57ee471d04480e0c9333b39e44980
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721892"
---
# <a name="set-verbose"></a>Задать verbose

Указывает, следует ли предоставлять подробный вывод при создании теневой копии. Если используется без параметров, команда **Set verbose** выводит справку из командной строки.

## <a name="syntax"></a>Синтаксис

```
set verbose {on | off}
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
|-----------|-------------|
|    {on    |    off}     |

## <a name="remarks"></a>Примечания

-   Если параметр verbose имеет значение ON, **параметр SET** предоставляет сведения о включении или исключении модуля записи, а также сведения о сжатии и извлечении метаданных.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)