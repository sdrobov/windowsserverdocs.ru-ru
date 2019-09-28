---
title: Exec
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 514503e4920e16ba6778185af32f925541805223
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377430"
---
# <a name="exec"></a>Exec



выполняет файл на локальном компьютере. Файл может быть сценарием **cmd** .

## <a name="syntax"></a>Синтаксис

```
exec <ScriptFile.cmd>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t -0ScriptFile. cmd >|Указывает файл скрипта для выполнения.|

## <a name="remarks"></a>Примечания

-   Эта команда используется для дублирования или восстановления данных в рамках последовательности резервного копирования или восстановления.
-   В случае сбоя скрипта возвращается ошибка, и сценарий DiskShadow завершает работу.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)