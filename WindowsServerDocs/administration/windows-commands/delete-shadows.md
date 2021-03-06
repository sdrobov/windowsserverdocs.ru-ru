---
title: delete shadows
description: Справочная статья по команде delete Shadows, которая удаляет теневые копии.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e29a84d2-04d1-4eb1-910a-5a47bddbc24d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6d541b50a78d738034204d14441352fff6c5d9fc
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85929509"
---
# <a name="delete-shadows"></a>delete shadows

Удаляет теневые копии.

## <a name="syntax"></a>Синтаксис

```
delete shadows [all | volume <volume> | oldest <volume> | set <setID> | id <shadowID> | exposed {<drive> | <mountpoint>}]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ---- | ---- |
| все | Удаляет все теневые копии. |
| тома`<volume>` | Удаляет все теневые копии данного тома. |
| Ранняя`<volume>` | Удаляет самую старую теневую копию заданного тома. |
| параметр`<setID>` | Удаляет теневые копии в наборе теневых копий заданного идентификатора. Псевдоним можно указать с помощью **%** символа, если он существует в текущей среде. |
| удостоверения`<shadowID>` | Удаляет теневую копию заданного идентификатора. Псевдоним можно указать с помощью **%** символа, если он существует в текущей среде. |
| предоставлено {'<drive> | <mountpoint>} |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [удалить команду](delete.md)
