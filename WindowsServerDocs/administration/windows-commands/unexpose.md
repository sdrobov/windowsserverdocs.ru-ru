---
title: Отмена доступа
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58dc7d0f-52e9-4587-9487-d3b4c3e52640
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fe9cb5dfd8ae6c71fdc72ddc1e8421229f98f5d0
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59837475"
---
# <a name="unexpose"></a>Отмена доступа



unexposes теневого копирования, который предоставляется с помощью **предоставлять** команды. Предоставленный теневой копии можно указать его идентификатор теневой, букву диска, общей папки или точки подключения.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
unexpose {<ShadowID> | <Drive:> | <Share> | <MountPoint>}
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Номер_теневой_копии >|Unexposes теневой копии, указанный с помощью заданного идентификатора тени.|
|\<Диск: >|Unexposes теневой копии, связанные с указанная буква диска (например, диск P).|
|\<Общий ресурс >|Unexposes теневой копии, связанные с указанной общей папке (например, \\ \\ *MachineName*\).|
|\<Точку подключения >|Unexposes теневой копии, связанные с указанную точку подключения (например, C:\shadowcopy\).|

## <a name="remarks"></a>Примечания

-   Вы можете использовать существующий псевдоним или переменную среды, вместо *Номер_теневой_копии*. Используйте **добавить** без параметров, чтобы просмотреть существующие псевдонимы.

## <a name="BKMK_examples"></a>Примеры

Чтобы отмените доступ к теневой копии, связанные с диска P, введите:
```
unexpose P:
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)