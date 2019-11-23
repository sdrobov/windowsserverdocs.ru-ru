---
ms.assetid: e5f55f3e-8d2a-4526-8d67-36a539126c22
title: Многоуровневое распределение fsutil
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 6863940d69e30f4984897a7e03369a834da21d1d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376781"
---
# <a name="fsutil-tiering"></a>Многоуровневое распределение fsutil
>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows 10

Включает управление функциями уровня хранилища, например установку и отключение флагов и списков уровней.

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
|клеарфлагс|Отключает флаги поведения уровней для тома.|
|\<> тома|Указывает том.|
|/трнх|Для томов с многоуровневое хранилищем может быть отключен сбор тепла.<br /><br>Применяется только к NTFS и ReFS.|
|куерифлагс|Запрашивает флаги поведения уровней тома.|
|регионлист|Список многоуровневых регионов тома и соответствующих им уровней хранилища.|
|сетфлагс|Включает флаги поведения уровней для тома.|
|тиерлист|Список уровней хранилища, связанных с томом.|


### <a name="examples"></a>Примеры.

Чтобы запросить флаги на томе C, введите:

```
fsutil tiering clearflags C:
```

Чтобы установить флаги на томе C, введите:

```
fsutil tiering setflags C: /TrNH
```

Чтобы сбросить флаги на томе C, введите:

```
fsutil tiering clearflags C: /TrNH
```

Чтобы получить список регионов тома C и соответствующих уровней хранилища, введите:

```
fsutil tiering regionlist C:
```

Чтобы получить список уровней тома C, введите:

```
fsutil tiering tierlist C:
```



### <a name="additional-references"></a>Дополнительная справка
[Условные обозначения синтаксиса команд командной строки](Command-Line-Syntax-Key.md)

[Fsutil](Fsutil.md)

