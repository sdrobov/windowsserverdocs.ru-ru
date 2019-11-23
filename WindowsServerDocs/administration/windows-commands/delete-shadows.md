---
title: удалить тени
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e29a84d2-04d1-4eb1-910a-5a47bddbc24d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c965af8b045c5ab3a110542d148b255f382a95c3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378627"
---
# <a name="delete-shadows"></a>удалить тени



Удаляет теневые копии.

## <a name="syntax"></a>Синтаксис

```
delete shadows [all | volume <Volume> | oldest <Volume> | set <SetID> | id <ShadowID> | exposed {<Drive> | <MountPoint>}]
```

## <a name="parameters"></a>Параметры

|     Параметр     |                                                                             Описание                                                                              |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        all        |                                                                      Удаляет все теневые копии.                                                                      |
| > тома \<тома  |                                                            Удаляет все теневые копии данного тома.                                                            |
| самый старый \<том >  |                                                         Удаляет самую старую теневую копию заданного тома.                                                          |
|   задать \<Сетид >    | Удаляет теневые копии в наборе теневых копий заданного идентификатора. Псевдоним можно указать с помощью **%** символа, если псевдоним существует в текущей среде. |
|  ID \<Шадовид >   |              Удаляет теневую копию заданного идентификатора. Псевдоним можно указать с помощью **%** символа, если псевдоним существует в текущей среде.               |
| предоставлено {\<диска > |                                                                            <MountPoint>}                                                                             |

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)