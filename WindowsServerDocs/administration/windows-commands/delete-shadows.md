---
title: удалить shadows
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 1a0945477bc4fce907b5ec4a697c7a2ec2f59557
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436117"
---
# <a name="delete-shadows"></a>удалить shadows



операции удаления теневых копий.

## <a name="syntax"></a>Синтаксис

```
delete shadows [all | volume <Volume> | oldest <Volume> | set <SetID> | id <ShadowID> | exposed {<Drive> | <MountPoint>}]
```

## <a name="parameters"></a>Параметры

|     Параметр     |                                                                             Описание                                                                              |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        all        |                                                                      Удаляет все теневые копии.                                                                      |
| том \<тома >  |                                                            Удаляет все теневые копии данного тома.                                                            |
| Самая старая \<тома >  |                                                         Удаляет старые копии данного тома.                                                          |
|   Задайте \<SetID >    | Удаляет теневые копии в теневого копирования наборе заданным идентификатором. Можно указать псевдоним с помощью **%** символов, если существует псевдоним в текущей среде. |
|  id \<ShadowID>   |              Удаляет теневую копию заданным идентификатором. Можно указать псевдоним с помощью **%** символов, если существует псевдоним в текущей среде.               |
| предоставляемые {\<диска > |                                                                            <MountPoint>}                                                                             |

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)