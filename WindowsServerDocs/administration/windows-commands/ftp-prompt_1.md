---
title: ftp prompt
description: Справочная статья по команде FTP Prompt, которая включает и выключает режим запроса.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 930df39b-45c4-4e0b-bfe2-1d1963be817a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dad75921ce6878d5a255edf92c5877238ffe899a
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86957596"
---
# <a name="ftp-prompt"></a>ftp prompt

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает и выключает режим запроса. По умолчанию режим подсказки включен. Если включен режим подсказки, команда FTP запрашивает во время нескольких передач файлов, позволяя выборочно получать или хранить файлы.

> [!NOTE]
> Вы можете использовать команды [FTP mget](ftp-mget.md) и [FTP мпут](ftp-mput_1.md) для перемещения всех файлов при отключенном режиме запроса.

## <a name="syntax"></a>Синтаксис

```
prompt
```

### <a name="examples"></a>Примеры

Чтобы включить или отключить режим подсказки, введите:

```
prompt
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Дополнительные рекомендации по FTP](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
