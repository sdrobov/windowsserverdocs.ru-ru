---
title: Целевой объект BdeHdCfg
description: Раздел команд Windows для BdeHdCfg Target — подготавливает раздел для использования в качестве системного диска с помощью BitLocker и восстановления Windows.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 2fb0a1daa257ef2c9f1cd77b88e5ef14f84a0dfa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382178"
---
# <a name="bdehdcfg-target"></a>BdeHdCfg: целевой объект



Подготавливает раздел для использования в качестве системного диска с помощью BitLocker и восстановления Windows. По умолчанию эта секция создается без буквы диска. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge}
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|по умолчанию|Указывает, что программа командной строки будет следовать тому же процессу, что и мастер установки BitLocker.|
|нераспределенного|Создает системный раздел из нераспределенного пространства, доступного на диске.|
|\<Буква_диска > сжимать|Сокращает диск, указанный объемом, необходимым для создания активного системного раздела. Чтобы использовать эту команду, на указанном диске должно быть не менее 5% свободного места.|
|\<Буква_диска > Merge|Использует диск, указанный в качестве активного системного раздела. Диск операционной системы не может быть целевым объектом для слияния.|

## <a name="BKMK_Examples"></a>Примеров

В следующем примере показано использование команды **Target** для обозначения существующего диска (P) в качестве системного диска.
```
bdehdcfg -target P: merge
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [BdeHdCfg](bdehdcfg.md)