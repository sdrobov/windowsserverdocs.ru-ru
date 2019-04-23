---
title: перезапуск bdehdcfg
description: Раздел Windows команды для перезагрузки bdehdcfg - сообщает bdehdcfg что после завершения подготовки диска следует перезагрузить компьютер.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 0f361db8fdf33bd414556575de75241f7dbd9327
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879465"
---
# <a name="bdehdcfg-restart"></a>bdehdcfg: restart



Информирует средство командной строки Bdehdcfg о том, что после завершения подготовки диска следует перезагрузить компьютер. Пример того, как эту команду можно использовать, см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge} -restart
```

### <a name="parameters"></a>Параметры

Эта команда не принимает дополнительные параметры.

## <a name="remarks"></a>Примечания

Если другие пользователи вошли компьютер и **quiet** команда не указана, будет отображаться приглашение для подтверждения того, что необходимо перезагрузить компьютер.

## <a name="BKMK_Examples"></a>Примеры

В следующем примере демонстрируется использование **перезапустите** команды.
```
bdehdcfg -target default -restart
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Bdehdcfg](bdehdcfg.md)