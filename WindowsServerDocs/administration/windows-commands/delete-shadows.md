---
title: удалить тени
description: Справочный раздел по удалению теней, который удаляет теневые копии.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e29a84d2-04d1-4eb1-910a-5a47bddbc24d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1dd367d76ad1699321af9caf47a0ddc351088a05
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720797"
---
# <a name="delete-shadows"></a>удалить тени

Удаляет теневые копии.

## <a name="syntax"></a>Синтаксис

```
delete shadows [all | volume <Volume> | oldest <Volume> | set <SetID> | id <ShadowID> | exposed {<Drive> | <MountPoint>}]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ---- | ---- |
| all | Удаляет все теневые копии. |
| > \<тома тома | Удаляет все теневые копии данного тома. |
| самый \<старый> тома | Удаляет самую старую теневую копию заданного тома. |
| задать \<> сетид | Удаляет теневые копии в наборе теневых копий заданного идентификатора. Псевдоним можно указать с помощью символа, **%** если он существует в текущей среде. |
| Идентификатор \<шадовид> | Удаляет теневую копию заданного идентификатора. Псевдоним можно указать с помощью символа, **%** если он существует в текущей среде. |
| предоставлено\<{Drive> | <MountPoint>} |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)