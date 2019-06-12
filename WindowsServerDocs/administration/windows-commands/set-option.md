---
title: Параметр SET
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d8d4921-9fdd-4a3c-bb0f-9df5458c4b84
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1c4756627d19d296d02fa11ac67ef80080ddf318
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66441367"
---
# <a name="set-option"></a>Параметр SET



Задает параметры для теневой копии. При использовании без параметров, **задания параметра** отображает справку в командной строке.

## <a name="syntax"></a>Синтаксис

```
set option {[differential | plex] [transportable] [[rollbackrecover] [txfrecover] | [noautorecover]]}
```

## <a name="parameters"></a>Параметры

|     Параметр     |                                                                                                  Описание                                                                                                  |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   [разностное   |                                                                                                     жных]                                                                                                     |
|  [переносимые]  |                       Указывает, что теневая копия не быть импортированы. CAB-файл метаданных можно использовать позже для импорта теневого копирования к тому же или другом компьютере.                       |
| [rollbackrecover] |                     Сигнализирует о разработчиков *автовосстановления* во время **PostSnapshot** событий. Это полезно, если теневая копия будет использоваться для отката (например, с помощью интеллектуального анализа данных).                      |
|   [txfrecover]    |                                                               Запросы VSS, чтобы сделать транзакционно согласованной копии во время создания.                                                                |
|  [noautorecover]  | Останавливает модулями записи и выполнять любые изменения теневой копии транзакционно согласованного состояния восстановления файловой системы. **Noautorecover** нельзя использовать с **txfrecover** или **rollbackrecover**. |

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)