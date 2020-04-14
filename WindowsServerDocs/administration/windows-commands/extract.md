---
title: extract
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 20dab03e-f6e1-4eb8-b8a1-fd6f1d97ee83
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d66682126f1cc3c924c42b4605a537a997e8ac52
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844777"
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
|источник|Сжатый файл (CAB-файл с одним файлом).|
|newname|Новое имя файла, чтобы получить извлеченный файл. Если значение не указано, используется исходное имя.|
|/A|Обработка всех ящиков. Ниже приведена цепочка CAB-файлов, начиная с первого указанного CAB-файла.|
|Ключей|Копировать исходный файл в место назначения (для копирования с дисков DMF).|
|/D|Откройте каталог CAB-файлов (используйте с именем filename, чтобы избежать извлечения).|
|/E|Extract (используйте вместо *.* для извлечения всех файлов).|
|/L dir|Расположение для размещения извлеченных файлов (по умолчанию текущий каталог).|
|/Y|Не выдавать запрос перед перезаписыванием существующего файла.|

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)