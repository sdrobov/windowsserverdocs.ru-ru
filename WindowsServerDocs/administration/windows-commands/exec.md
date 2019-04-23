---
title: EXEC
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 364e8baf-576f-401b-a431-7d3c06621614
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ecdfd05b8abefb35946b783daaa3220a6713a38d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882925"
---
# <a name="exec"></a>EXEC



выполняет файл на локальном компьютере. Файл может быть **cmd** скрипта.

## <a name="syntax"></a>Синтаксис

```
exec <ScriptFile.cmd>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<ScriptFile.cmd >|Определяет файл сценария для выполнения.|

## <a name="remarks"></a>Примечания

-   Эта команда позволяет дублировать или восстановить данные как часть резервной копии или последовательность восстановления.
-   Если сценарий завершится ошибкой, возвращается ошибка, и программа DiskShadow завершает работу.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)