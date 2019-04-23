---
title: quiet bdehdcfg
description: Разделе команд Windows для скрытый bdehdcfg - сообщает bdehdcfg, чтобы не отображать всех действий и ошибок.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 0f0d98f6ae76e9bf6357689c97e091766b9645c2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59865755"
---
# <a name="bdehdcfg-quiet"></a>bdehdcfg: quiet



Информирует Bdehdcfg программой командной строки для всех действий и ошибок, не для отображения в интерфейсе командной строки. Пример того, как эту команду можно использовать, см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge} -quiet
```

### <a name="parameters"></a>Параметры

Эта команда не принимает дополнительные параметры.

## <a name="remarks"></a>Примечания

Если Да, любой/без вывода сообщений (Y/N) были отображались бы во время подготовки диска, предполагается ответ «Да». Чтобы просмотреть любой ошибки, возникшей во время подготовки диска, просмотрите журнал системных событий в разделе **Microsoft-Windows-BitLocker-DrivePreparationTool** поставщика событий.

## <a name="BKMK_Examples"></a>Примеры

В следующем примере демонстрируется использование **quiet** команды.
```
bdehdcfg -target default -quiet
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Bdehdcfg](bdehdcfg.md)