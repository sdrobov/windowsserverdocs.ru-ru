---
ms.assetid: 385a2a7c-d6bd-4f11-9c18-fca0413f9e97
title: Fsutil dirty
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 3b35938c21180199aabb74431d20a31167aea706
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725530"
---
# <a name="fsutil-dirty"></a>Fsutil dirty
> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Запрашивает или устанавливает «грязный» бит тома. Если задан «грязный» бит тома, то **Autochk** автоматически проверяет том на наличие ошибок при следующем перезапуске компьютера.



## <a name="syntax"></a>Синтаксис

```
fsutil dirty {query | set} <VolumePath>
```

### <a name="parameters"></a>Параметры

|   Параметр   |                                                 Описание                                                  |
|---------------|--------------------------------------------------------------------------------------------------------------|
|     query     |                                  Запрашивает «грязный» бит указанного тома.                                   |
|      set      |                                    Задает "грязный" бит указанного тома.                                    |
| \<VolumePath> | Указывает имя диска, за которым следует двоеточие или GUID в следующем формате: **том {**<em>GUID</em>**}**. |

## <a name="remarks"></a>Примечания

-   «Грязный» бит тома означает, что файловая система может находиться в нестабильном состоянии. "Грязный" бит можно задать по следующим причинам:

    -   Том находится в режиме "в сети" и содержит необработанные изменения.

    -   Внесены изменения в том, и компьютер был завершен до того, как изменения были зафиксированы на диске.

    -   На томе обнаружено повреждение.

-   Если «грязный» бит задан при перезапуске компьютера, **chkdsk** запускается для проверки целостности файловой системы и попыток устранения любых проблем с томом.

## <a name="examples"></a><a name="BKMK_examples"></a>Примеры
Чтобы запросить "грязный" бит на диске C, введите:

```
fsutil dirty query c:
```

-   Если том изменен, отображается следующий результат:

    `Volume C: is dirty`

-   Если том не является "грязным", в следующем выводе отображаются следующие данные:

    `Volume C: is not dirty`

Чтобы установить «грязный» бит на диске C, введите:

```
fsutil dirty set C:
```

## <a name="additional-references"></a>Дополнительные ссылки
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Fsutil](Fsutil.md)


