---
title: fsutil tiering
description: Справочный раздел по многоуровневой команде fsutil, который обеспечивает управление функциями уровня хранилища, например установку и отключение флагов и списков уровней.
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: e5f55f3e-8d2a-4526-8d67-36a539126c22
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 6fa8646dcdf7e836ccb45f253e0c4f8691b1ea3c
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436849"
---
# <a name="fsutil-tiering"></a>fsutil tiering

> Применяется к: Windows Server (Semi-Annual Channel), Windows Server 2019, Windows Server 2016, Windows 10

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

| Параметр | Описание |
| --------- | ----------- |
| клеарфлагс | Отключает флаги поведения уровней для тома. |
| `<volume>` | Указывает том. |
| /трнх | Для томов с многоуровневое хранилищем может быть отключен сбор тепла.<p>Применяется только к NTFS и ReFS. |
| куерифлагс | Запрашивает флаги поведения уровней тома. |
| регионлист | Список многоуровневых регионов тома и соответствующих им уровней хранилища. |
| сетфлагс | Включает флаги поведения уровней для тома. |
| тиерлист | Список уровней хранилища, связанных с томом. |

### <a name="examples"></a>Примеры

Чтобы запросить флаги на томе C, введите:

```
fsutil tiering clearflags C:
```

Чтобы установить флаги на томе C, введите:

```
fsutil tiering setflags C: /trnh
```

Чтобы сбросить флаги на томе C, введите:

```
fsutil tiering clearflags C: /trnh
```

Чтобы получить список регионов тома C и соответствующих уровней хранилища, введите:

```
fsutil tiering regionlist C:
```

Чтобы получить список уровней тома C, введите:

```
fsutil tiering tierlist C:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [fsutil](fsutil.md)
