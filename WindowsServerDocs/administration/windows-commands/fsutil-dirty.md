---
title: fsutil dirty
description: Справочная статья по команде fsutil dirty, которая запрашивает или устанавливает «грязный» бит тома.
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: 385a2a7c-d6bd-4f11-9c18-fca0413f9e97
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: c61ab5405fb5b469b6f4513459e4096524f4b7fe
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85929265"
---
# <a name="fsutil-dirty"></a>fsutil dirty

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8

Запрашивает или устанавливает «грязный» бит тома. Если задан «грязный» бит тома, то **Autochk** автоматически проверяет том на наличие ошибок при следующем перезапуске компьютера.

## <a name="syntax"></a>Синтаксис

```
fsutil dirty {query | set} <volumepath>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| query | Запрашивает «грязный» бит указанного тома. |
| set | Задает "грязный" бит указанного тома. |
| `<volumepath>` | Указывает имя диска, за которым следует двоеточие или GUID в следующем формате: `volume{GUID}` . |

#### <a name="remarks"></a>Комментарии

- «Грязный» бит тома означает, что файловая система может находиться в нестабильном состоянии. "Грязный" бит можно задать по следующим причинам:

    - Том находится в режиме "в сети" и содержит необработанные изменения.

    - Внесены изменения в том, и компьютер был завершен до того, как изменения были зафиксированы на диске.

    - На томе обнаружено повреждение.

- Если «грязный» бит задан при перезапуске компьютера, **chkdsk** запускается для проверки целостности файловой системы и попыток устранения любых проблем с томом.

### <a name="examples"></a>Примеры

Чтобы запросить "грязный" бит на диске C, введите:

```
fsutil dirty query c:
```

    If the volume is dirty, the following output displays:

    `Volume C: is dirty`

    If the volume isn't dirty, the following output displays:

    `Volume C: is not dirty`

Чтобы установить «грязный» бит на диске C, введите:

```
fsutil dirty set C:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [fsutil](fsutil.md)
