---
title: exec
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 364e8baf-576f-401b-a431-7d3c06621614
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f10e28a8da96bc7228af4561fb36824899f2d7a4
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725745"
---
# <a name="exec"></a>exec



Выполняет файл на локальном компьютере. Файл может быть сценарием **cmd** .

## <a name="syntax"></a>Синтаксис

```
exec <ScriptFile.cmd>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<ScriptFile. cmd>|Указывает файл скрипта для выполнения.|

## <a name="remarks"></a>Примечания

-   Эта команда используется для дублирования или восстановления данных в рамках последовательности резервного копирования или восстановления.
-   В случае сбоя скрипта возвращается ошибка, и сценарий DiskShadow завершает работу.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)