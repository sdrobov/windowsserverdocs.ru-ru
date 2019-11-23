---
title: BdeHdCfg невдривелеттер
description: Раздел команд Windows для BdeHdCfg невдривелеттер. назначает новую букву диска части диска, используемой в качестве системного диска.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f1f200a0-6850-4f0d-9047-f9f982a590f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e2abd4a686f358b5dd844514735edb3ffaa13845
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382233"
---
# <a name="bdehdcfg-newdriveletter"></a>BdeHdCfg: невдривелеттер



Назначает новую букву диска части диска, используемой в качестве системного диска. Пример того, как можно использовать эту команду, см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge} -newdriveletter <DriveLetter>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Буква_диска >|Определяет букву диска, которая будет назначена указанному целевому диску.|

## <a name="remarks"></a>Замечания

Рекомендуется не назначать диску букву диска системному накопителю.

## <a name="BKMK_Examples"></a>Примеров

В следующем примере показано, что диску по умолчанию назначается буква P.
```
bdehdcfg -target default -newdriveletter P:
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [BdeHdCfg](bdehdcfg.md)