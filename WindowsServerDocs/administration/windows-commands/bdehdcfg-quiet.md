---
title: BdeHdCfg quiet
description: Раздел команд Windows для BdeHdCfg quiet — указывает BdeHdCfg отобразить все действия и ошибки.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f75b702-890b-4ff9-805c-edf5cadd8822
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d59a14e34200e3fa8e18e36e166ef62ceca1afe7
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382216"
---
# <a name="bdehdcfg-quiet"></a>BdeHdCfg: тихий режим



Информирует программу командной строки BdeHdCfg о том, что все действия и ошибки не должны отображаться в интерфейсе командной строки. Пример того, как можно использовать эту команду, см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge} -quiet
```

### <a name="parameters"></a>Параметры

Эта команда не принимает дополнительных параметров.

## <a name="remarks"></a>Примечания

Если при подготовке диска отображались любые запросы да/нет (Y/N), предполагается ответ "Да". Чтобы просмотреть ошибки, возникшие во время подготовки диска, просмотрите журнал системных событий в поставщике событий **Microsoft-Windows-BitLocker-дривепрепаратионтул** .

## <a name="BKMK_Examples"></a>Примеров

В следующем примере показано использование команды **quiet** .
```
bdehdcfg -target default -quiet
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [BdeHdCfg](bdehdcfg.md)