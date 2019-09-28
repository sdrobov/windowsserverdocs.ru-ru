---
title: перезапустить BdeHdCfg
description: Раздел команд Windows для перезапуска BdeHdCfg — указывает BdeHdCfg, что компьютер должен быть перезагружен после завершения подготовки диска.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a98b76bb-36f1-4790-b337-7dc35f606bc6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e6c4e48b051f567c98ea679feaa22f995982a899
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382209"
---
# <a name="bdehdcfg-restart"></a>BdeHdCfg: перезапуск



Информирует программу командной строки BdeHdCfg о том, что компьютер должен быть перезагружен после завершения подготовки диска. Пример того, как можно использовать эту команду, см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge} -restart
```

### <a name="parameters"></a>Параметры

Эта команда не принимает дополнительных параметров.

## <a name="remarks"></a>Примечания

Если другие пользователи вошли в систему, а команда **quiet** не указана, появится запрос на подтверждение перезагрузки компьютера.

## <a name="BKMK_Examples"></a>Примеров

В следующем примере показано использование команды **restart** .
```
bdehdcfg -target default -restart
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [BdeHdCfg](bdehdcfg.md)