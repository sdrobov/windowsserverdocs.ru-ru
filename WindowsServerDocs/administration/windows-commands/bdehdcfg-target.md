---
title: целевой объект bdehdcfg
description: Разделе команд Windows для целевого объекта bdehdcfg - подготавливает секции для использования в качестве системного диска путем восстановления BitLocker и Windows.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f761d25d-8349-4ac7-ac46-6bb340a4348f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f8d180974f480b4c40532dab529ad49dcc33540d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59881535"
---
# <a name="bdehdcfg-target"></a>Bdehdcfg: целевой объект



Подготавливает секции для использования в качестве системного диска BitLocker и восстановления Windows. По умолчанию эта секция создается без буквы диска. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge}
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|значение по умолчанию|Указывает, что средство командной строки последует за тот же процесс, что мастер установки BitLocker.|
|Нераспределенное|Создает системный раздел недостаточно нераспределенного места на диске.|
|\<Буква диска > сжатия|Уменьшает указанный диск на величину, необходимо создать раздел активной системы. Чтобы использовать эту команду, указанный диск должен иметь по крайней мере 5 процентов свободного места.|
|\<Буква диска > слияния|Использует диске, указанном в качестве активного системного раздела. Диск операционной системы не может быть целевой для слияния.|

## <a name="BKMK_Examples"></a>Примеры

В следующем примере показана с помощью **целевой** команду, чтобы назначить существующему диску (P) в качестве системного диска.
```
bdehdcfg -target P: merge
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Bdehdcfg](bdehdcfg.md)