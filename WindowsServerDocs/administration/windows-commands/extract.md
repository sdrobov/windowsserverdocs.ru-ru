---
title: extract
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 20dab03e-f6e1-4eb8-b8a1-fd6f1d97ee83
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1cca89a356530e49fbf2b0610ff3ced1c5733847
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725654"
---
# <a name="extract"></a>extract



## <a name="syntax"></a>Синтаксис

```
EXTRACT [/Y] [/A] [/D | /E] [/L dir] cabinet [filename ...]
EXTRACT [/Y] source [newname]
EXTRACT [/Y] /C source destination
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|файле|Файл содержит два или более файлов.|
|filename|Имя файла, извлекаемого из CAB-архива. Можно использовать подстановочные знаки и несколько имен файлов (разделенные пробелами).|
|source|Сжатый файл (CAB-файл с одним файлом).|
|newname|Новое имя файла, чтобы получить извлеченный файл. Если значение не указано, используется исходное имя.|
|/A|Обработка всех ящиков. Ниже приведена цепочка CAB-файлов, начиная с первого указанного CAB-файла.|
|/C|Копировать исходный файл в место назначения (для копирования с дисков DMF).|
|/D|Откройте каталог CAB-файлов (используйте с именем filename, чтобы избежать извлечения).|
|/E|Extract (используйте вместо *.* для извлечения всех файлов).|
|/L dir|Расположение для размещения извлеченных файлов (по умолчанию текущий каталог).|
|/Y|Не выдавать запрос перед перезаписыванием существующего файла.|

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)