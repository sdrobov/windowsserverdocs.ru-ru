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
ms.openlocfilehash: cf3685bae9ed76ede4da6df244139437d92250c0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844337"
---
# <a name="fsutil-dirty"></a>Fsutil dirty
>Область применения: Windows Server (половина ежегодного канала), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Запрашивает или устанавливает «грязный» бит тома. Если задан «грязный» бит тома, то **Autochk** автоматически проверяет том на наличие ошибок при следующем перезапуске компьютера.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
fsutil dirty {query | set} <VolumePath>
```

### <a name="parameters"></a>Параметры

|   Параметр   |                                                 Описание                                                  |
|---------------|--------------------------------------------------------------------------------------------------------------|
|     query     |                                  Запрашивает «грязный» бит указанного тома.                                   |
|      set      |                                    Задает "грязный" бит указанного тома.                                    |
| \<VolumePath > | Указывает имя диска, за которым следует двоеточие или GUID в следующем формате: **том {** <em>GUID</em> **}** . |

## <a name="remarks"></a>Примечания

-   «Грязный» бит тома означает, что файловая система может находиться в нестабильном состоянии. "Грязный" бит можно задать по следующим причинам:

    -   Том находится в режиме "в сети" и содержит необработанные изменения.

    -   Внесены изменения в том, и компьютер был завершен до того, как изменения были зафиксированы на диске.

    -   На томе обнаружено повреждение.

-   Если «грязный» бит задан при перезапуске компьютера, **chkdsk** запускается для проверки целостности файловой системы и попыток устранения любых проблем с томом.

## <a name="examples"></a><a name="BKMK_examples"></a>Примеров
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

## <a name="additional-references"></a>Дополнительные материалы
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Fsutil](Fsutil.md)


