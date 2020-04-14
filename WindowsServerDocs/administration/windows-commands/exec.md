---
title: Exec
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 364e8baf-576f-401b-a431-7d3c06621614
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d39fbf948050dd00f329e461c34c2365030cb05d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844997"
---
# <a name="exec"></a>Exec



выполняет файл на локальном компьютере. Файл может быть сценарием **cmd** .

## <a name="syntax"></a>Синтаксис

```
exec <ScriptFile.cmd>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<ScriptFile. cmd >|Указывает файл скрипта для выполнения.|

## <a name="remarks"></a>Примечания

-   Эта команда используется для дублирования или восстановления данных в рамках последовательности резервного копирования или восстановления.
-   В случае сбоя скрипта возвращается ошибка, и сценарий DiskShadow завершает работу.

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)