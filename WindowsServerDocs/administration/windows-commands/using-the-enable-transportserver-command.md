---
title: Enable-Транспортсервер
description: Справочный раздел по Enable-Транспортсервер, который включает все службы для транспортного сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9d79dba1-4b57-4a00-8cba-877e6b8618e6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 50cc381b1c178628be7d135868027b4f37787cdd
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720923"
---
# <a name="enable-transportserver"></a>Enable-Транспортсервер

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает все службы для транспортного сервера.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Enable-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя транспортного сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя не указано, будет использоваться локальный сервер.|
## <a name="examples"></a>Примеры
Чтобы включить службы на сервере, выполните одно из следующих действий.
```
wdsutil /Enable-TransportServer
wdsutil /verbose /Enable-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ](command-line-syntax-key.md)
синтаксиса
командной строки[с помощью команды Disable-транспортсервер](using-the-disable-transportserver-command.md)[с командой Get-транспортсервер](using-the-get-transportserver-command.md)
[: Set-транспортсервер](subcommand-set-transportserver.md)
подкоманда:[Start-транспортсервер](subcommand-start-transportserver.md)
[подкоманда:-транспортсервер](subcommand-stop-transportserver.md)
