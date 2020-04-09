---
ms.assetid: 6c6ff819-f349-4aea-b0be-1f637f631736
title: Fsutil WIM
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: d4a8f2c008c1a28e498edb7726a8c209e91f41af
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843927"
---
# <a name="fsutil-wim"></a>Fsutil WIM
>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows 10

Предоставляет функции для обнаружения и управления файлами, поддерживающими образ Windows (WIM).

## <a name="syntax"></a>Синтаксис

```
fsutil wim [enumfiles] <drive name> <data source>
fsutil wim [enumwims] <drive name>
fsutil wim [queryfile] <filename>
fsutil wim [removewim] <drive name> <data source>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|енумфилес|Перечисляет файлы с резервным копированием WIM.|
|\<имя диска >|Указывает имя диска.|
|\<> источника данных|Указывает источник данных.|
|енумвимс|Перечисляет резервные WIM-файлы.|
|куерифиле|Запросы, если файл поддерживается WIM, и, если это так, отображает сведения о WIM-файле.|
|\<имя файла >|Указывает имя файла.|
|ремовевим|Удаляет WIM из резервных файлов.|




### <a name="examples"></a>Примеры

Чтобы перечислить файлы для диска C: из источника данных 0, введите:

```
fsutil wim enumfiles C: 0
```

Чтобы перечислить резервные WIM-файлы для диска C:, введите:

```
fsutil wim enumwims C:
```

Чтобы узнать, поддерживается ли файл WIM, введите:

```
fsutil wim C:\Windows\Notepad.exe
```

Чтобы удалить WIM из резервных файлов для тома C: и источника данных 2, введите:

```
fsutil wim removewims C: 2
```

### <a name="additional-references"></a>Дополнительная справка
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Fsutil](Fsutil.md)