---
ms.assetid: e5f55f3e-8d2a-4526-8d67-36a539126c22
title: Распределение по уровням fsutil
ms.prod: windows-server-threshold
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: dcb69e4e9c71a723bfd735eb7915472f1232a92b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59859255"
---
# <a name="fsutil-tiering"></a>Распределение по уровням fsutil
>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10

Позволяет управлять функции уровней хранилища, такие как установка, отключение флагов и список уровней.

## <a name="syntax"></a>Синтаксис

```
fsutil tiering [clearflags] <volume> <flags>
fsutil tiering [queryflags] <volume>
fsutil tiering [regionlist] <volume>
fsutil tiering [setflags] <volume> <flags>
fsutil tiering [tierlist] <volume>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|ClearFlags|Отключает флаги распределения по уровням поведения тома.|
|\<Тома >|Указывает том.|
|/TrNH|Для томов с многоуровневого хранилища приводит к тепловой сбора должно быть отключено.<br /><br>Применяется только к NTFS и ReFS.|
|queryflags|Запрашивает по уровням флаги поведения тома.|
|regionlist|Список регионов многоуровневого тома и их уровни соответствующего хранилища.|
|SetFlags|Включает флаги распределения по уровням поведения тома.|
|tierlist|Список tieres хранения, связанную с томом.|


### <a name="examples"></a>Примеры

Чтобы запросить флаги на томе C, введите следующую команду:

```
fsutil tiering clearflags C:
```

Чтобы задать флаги на томе C, введите:

```
fsutil tiering setflags C: /TrNH
```

Чтобы очистить флаги на томе C, введите следующую команду:

```
fsutil tiering clearflags C: /TrNH
```

Чтобы получить список регионов тома C и их уровни соответствующего хранилища, введите:

```
fsutil tiering regionlist C:
```

Чтобы получить список уровней тома C, введите следующую команду:

```
fsutil tiering tierlist C:
```



### <a name="additional-references"></a>Дополнительная справка
[Ключ синтаксиса командной строки](Command-Line-Syntax-Key.md)

[fsutil](Fsutil.md)

