---
title: BdeHdCfg quiet
description: Команды Windows для **BdeHdCfg quiet**, которые сообщают BdeHdCfg о том, что не отображаются все действия и ошибки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7f75b702-890b-4ff9-805c-edf5cadd8822
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e9c24d8861476e6c1578af8245236d699b6ef6db
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851047"
---
# <a name="bdehdcfg-quiet"></a>BdeHdCfg: тихий режим

Информирует программу командной строки BdeHdCfg о том, что все действия и ошибки не должны отображаться в интерфейсе командной строки. Пример того, как можно использовать эту команду, см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge} -quiet
```

#### <a name="parameters"></a>Параметры

Эта команда не принимает дополнительных параметров.

## <a name="remarks"></a>Примечания

Если при подготовке диска отображались любые запросы да/нет (Y/N), предполагается ответ "Да". Чтобы просмотреть ошибки, возникшие во время подготовки диска, просмотрите журнал системных событий в поставщике событий **Microsoft-Windows-BitLocker-дривепрепаратионтул** .

## <a name="examples"></a><a name="BKMK_Examples"></a>Примеров

В следующем примере показано использование команды **quiet** .

```
bdehdcfg -target default -quiet
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [BdeHdCfg](bdehdcfg.md)