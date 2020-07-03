---
title: bdehdcfg quiet
description: Справочная статья по команде BdeHdCfg quiet, которая указывает, что BdeHdCfg не отображает все действия и ошибки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7f75b702-890b-4ff9-805c-edf5cadd8822
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5b6a62314109d1c299187d87fba23b8e59669d66
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923457"
---
# <a name="bdehdcfg-quiet"></a>BdeHdCfg: тихий режим

Информирует программу командной строки BdeHdCfg о том, что все действия и ошибки не должны отображаться в интерфейсе командной строки. Любые запросы да/нет (Y/N), отображаемые во время подготовки диска, принимают ответ "Да". Чтобы просмотреть ошибки, возникшие во время подготовки диска, просмотрите журнал системных событий в поставщике событий **Microsoft-Windows-BitLocker-дривепрепаратионтул** .

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge} -quiet
```

#### <a name="parameters"></a>Параметры

У этой команды нет дополнительных параметров.

## <a name="examples"></a>Примеры

Чтобы использовать команду **quiet** , выполните следующие действия:

```
bdehdcfg -target default -quiet
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
