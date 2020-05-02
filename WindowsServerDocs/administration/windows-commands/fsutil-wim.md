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
ms.openlocfilehash: 12a9965515ef26e0cbccb2d20d25f66b54b23b8a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720063"
---
# <a name="fsutil-wim"></a>Fsutil WIM
> Применяется к: Windows Server (Semi-Annual Channel), Windows Server 2019, Windows Server 2016, Windows 10

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
|\<имя диска>|Указывает имя диска.|
|\<> источника данных|Указывает источник данных.|
|енумвимс|Перечисляет резервные WIM-файлы.|
|куерифиле|Запросы, если файл поддерживается WIM, и, если это так, отображает сведения о WIM-файле.|
|\<имя файла>|Указывает имя файла.|
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