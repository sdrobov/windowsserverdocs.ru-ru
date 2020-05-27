---
title: ремотехелп FTP
description: Справочный раздел по команде FTP ремотехелп, который отображает справку по удаленным командам.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ef23adf3-ead4-44c8-ac1d-c8a6f4b2bf73
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 659de5487890b50aab9004f650e4584085e7306c
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820324"
---
# <a name="ftp-remotehelp"></a>ремотехелп FTP

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает справку по удаленным командам.

## <a name="syntax"></a>Синтаксис

```
remotehelp [<command>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ------- | -------- |
| `[<command>]` | Указывает имя команды, для которой требуется справка. Если `<command>` не указан, эта команда отображает список всех удаленных команд. Можно также выполнять удаленные команды с помощью [предложения FTP](ftp-quote.md) или [литерала FTP](ftp-literal_1.md). |

### <a name="examples"></a>Примеры

Чтобы отобразить список удаленных команд, введите:

```
remotehelp
```

Чтобы отобразить синтаксис удаленной команды *достижением* , введите:

```
remotehelp feat
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Цитата FTP](ftp-quote.md)

- [литерал FTP](ftp-literal_1.md)

- [Дополнительные рекомендации по FTP](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
