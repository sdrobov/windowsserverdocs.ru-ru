---
title: извлечь
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 20dab03e-f6e1-4eb8-b8a1-fd6f1d97ee83
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9113c34b61b98fb738bc0aff03193ab73b1abbd7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882315"
---
# <a name="extract"></a>извлечь



## <a name="syntax"></a>Синтаксис

```
EXTRACT [/Y] [/A] [/D | /E] [/L dir] cabinet [filename ...]
EXTRACT [/Y] source [newname]
EXTRACT [/Y] /C source destination
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|CAB-файла|Файл содержит два или более файлов.|
|имя_файла|Имя файла для извлечения из CAB-файла. Можно использовать подстановочные знаки и несколько файлов (разделенных пробелами).|
|источник|Сжатый файл (CAB-файл с только одним файлом).|
|newname|Новое имя файла извлеченного файла. Если не указан, используется исходное имя.|
|/A|Обработать все CAB-файлы. CAB-цепочка начиная с первого CAB-файл упомянутых.|
|/C|Скопируйте исходный файл в место назначения (для копирования из DMF дисков).|
|/D|Открыть CAB-каталог (используйте файл с именем, чтобы избежать извлечения).|
|/E|Извлеките (используйте вместо *.* для извлечения всех файлов).|
|Dir/l|Расположение следует поместить извлеченные файлы (по умолчанию — текущий каталог).|
|/Y|Не запрашивать перед перезаписью существующего файла.|

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)