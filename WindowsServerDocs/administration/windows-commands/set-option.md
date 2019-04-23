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
ms.openlocfilehash: 81678768bb2b5fcfd7f2f2d067562e78e93dc549
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59848855"
---
# <a name="set-option"></a>Параметр SET



Задает параметры для теневой копии. При использовании без параметров, **задания параметра** отображает справку в командной строке.

## <a name="syntax"></a>Синтаксис

```
set option {[differential | plex] [transportable] [[rollbackrecover] [txfrecover] | [noautorecover]]}
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[разностное | жных]|Тип поставщика теневого копирования для создания.|
|[переносимые]|Указывает, что теневая копия не быть импортированы. CAB-файл метаданных можно использовать позже для импорта теневого копирования к тому же или другом компьютере.|
|[rollbackrecover]|Сигнализирует о разработчиков *автовосстановления* во время **PostSnapshot** событий. Это полезно, если теневая копия будет использоваться для отката (например, с помощью интеллектуального анализа данных).|
|[txfrecover]|Запросы VSS, чтобы сделать транзакционно согласованной копии во время создания.|
|[noautorecover]|Останавливает модулями записи и выполнять любые изменения теневой копии транзакционно согласованного состояния восстановления файловой системы. **Noautorecover** нельзя использовать с **txfrecover** или **rollbackrecover**.|

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)