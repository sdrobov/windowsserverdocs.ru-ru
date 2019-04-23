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
ms.openlocfilehash: 4b0d5414cb5b60face5245d7ea22d66c8629bfcb
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873735"
---
# <a name="delete-shadows"></a>удалить shadows



операции удаления теневых копий.

## <a name="syntax"></a>Синтаксис

```
delete shadows [all | volume <Volume> | oldest <Volume> | set <SetID> | id <ShadowID> | exposed {<Drive> | <MountPoint>}]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|all|Удаляет все теневые копии.|
|том \<тома >|Удаляет все теневые копии данного тома.|
|Самая старая \<тома >|Удаляет старые копии данного тома.|
|Задайте \<SetID >|Удаляет теневые копии в теневого копирования наборе заданным идентификатором. Можно указать псевдоним с помощью **%** символов, если существует псевдоним в текущей среде.|
|id \<ShadowID>|Удаляет теневую копию заданным идентификатором. Можно указать псевдоним с помощью **%** символов, если существует псевдоним в текущей среде.|
|предоставляемые {\<диска > | <MountPoint>}|Удаляет теневую копию, представленные на указанном диске букву или точку подключения. Укажите точки подключения, как c:\mountPoint или с помощью буквы диска, например p:.|

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)