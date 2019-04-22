---
ms.assetid: 6c6ff819-f349-4aea-b0be-1f637f631736
title: fsutil wim
ms.prod: windows-server-threshold
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: c9186721ce4d3a549964e420cbc16d4893a1859d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59826045"
---
# <a name="fsutil-wim"></a>fsutil wim
>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10

Предоставляет функции для обнаружения и управления файлами на основе образа WIM Windows.

## <a name="syntax"></a>Синтаксис

```
fsutil wim [enumfiles] <drive name> <data source>
fsutil wim [enumwims] <drive name>
fsutil wim [queryfile] <filename>
fsutil wim [removewim] <drive name> <data source>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|enumfiles|Перечисляет резервного WIM-файлов.|
|\<Имя диска >|Указывает имя диска.|
|\<источник данных >|Указывает источник данных.|
|enumwims|Перечисляет резервного WIM-файлов.|
|queryfile|Запросы, если для файла WIM и если да, отображает сведения о WIM-файле.|
|\<Имя файла >|Указывает имя файла.|
|removewim|Отменяет архивирование файлов WIM.|




### <a name="examples"></a>Примеры

Чтобы перечислить файлы для диска C: из источника данных 0, введите следующую команду:

```
fsutil wim enumfiles C: 0
```

Чтобы перечислить резервного WIM-файлов для диска C:, введите следующую команду:

```
fsutil wim enumwims C:
```

Чтобы увидеть, если файл поддерживаемый WIM, введите:

```
fsutil wim C:\Windows\Notepad.exe
```

Чтобы удалить WIM из архивирование файлов для тома C: и источник данных 2, введите следующую команду:

```
fsutil wim removewims C: 2
```

### <a name="additional-references"></a>Дополнительная справка
[Ключ синтаксиса командной строки](Command-Line-Syntax-Key.md)

[fsutil](Fsutil.md)