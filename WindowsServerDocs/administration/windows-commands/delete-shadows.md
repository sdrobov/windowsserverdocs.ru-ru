---
title: удалить тени
description: Команды Windows для удаления теней, которые удаляют теневые копии.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e29a84d2-04d1-4eb1-910a-5a47bddbc24d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cd109f7ddc0365d03737eddba31a1a4b7f34915b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846567"
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
| > тома \<тома | Удаляет все теневые копии данного тома. |
| самый старый \<том > | Удаляет самую старую теневую копию заданного тома. |
| задать \<Сетид > | Удаляет теневые копии в наборе теневых копий заданного идентификатора. Псевдоним можно указать с помощью **%** символа, если псевдоним существует в текущей среде. |
| ID \<Шадовид > | Удаляет теневую копию заданного идентификатора. Псевдоним можно указать с помощью **%** символа, если псевдоним существует в текущей среде. |
| предоставлено {\<диска > | <MountPoint>} |

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)