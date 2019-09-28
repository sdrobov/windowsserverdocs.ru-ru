---
title: извлечь
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 967f08e271019cc33970419179c9ddbf902b1882
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377260"
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
|файле|Файл содержит два или более файлов.|
|имя_файла|Имя файла, извлекаемого из CAB-архива. Можно использовать подстановочные знаки и несколько имен файлов (разделенные пробелами).|
|источник|Сжатый файл (CAB-файл с одним файлом).|
|newname|Новое имя файла, чтобы получить извлеченный файл. Если значение не указано, используется исходное имя.|
|/|Обработка всех ящиков. Ниже приведена цепочка CAB-файлов, начиная с первого указанного CAB-файла.|
|КЛЮЧЕЙ|Копировать исходный файл в место назначения (для копирования с дисков DMF).|
|/D|Откройте каталог CAB-файлов (используйте с именем filename, чтобы избежать извлечения).|
|/E|Extract (используйте вместо *.* для извлечения всех файлов).|
|/L dir|Расположение для размещения извлеченных файлов (по умолчанию текущий каталог).|
|/Y|Не выдавать запрос перед перезаписыванием существующего файла.|

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)