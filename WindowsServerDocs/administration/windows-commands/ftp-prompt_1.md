---
title: запрос FTP
description: Справочный раздел для команды FTP Prompt, которая переключает режим запроса и включает его.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 930df39b-45c4-4e0b-bfe2-1d1963be817a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 57f0e1eead36665c19845944bf22325b1aecebbb
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820384"
---
# <a name="ftp-prompt"></a>запрос FTP

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

- [Дополнительные рекомендации по FTP](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
