---
title: ftp remotehelp
description: Справочная статья по команде FTP ремотехелп, которая отображает справку по удаленным командам.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ef23adf3-ead4-44c8-ac1d-c8a6f4b2bf73
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7edfcdadf777dbff062665831fdc2aee3139ec6e
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86957490"
---
# <a name="ftp-remotehelp"></a>ftp remotehelp

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

- [ftp quote](ftp-quote.md)

- [ftp literal](ftp-literal_1.md)

- [Дополнительные рекомендации по FTP](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
