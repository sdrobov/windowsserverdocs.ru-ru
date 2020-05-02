---
title: Disable-Транспортсервер
description: Справочный раздел по Disable-Транспортсервер, который отключает все службы для транспортного сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a009706b-8e89-486b-8e3d-512cd9f4de74
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 81ae150b4f8e4de577e377a2d10a7a69675adac7
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720956"
---
# <a name="disable-transportserver"></a>Disable-Транспортсервер

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отключает все службы для транспортного сервера.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Disable-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя транспортного сервера, который должен быть отключен. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя транспортного сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a>Примеры
Чтобы отключить сервер, введите:
```
wdsutil /Disable-TransportServer
wdsutil /verbose /Disable-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ](command-line-syntax-key.md)
синтаксиса командной строки[с помощью команды](using-the-enable-transportserver-command.md)
Enable-транспортсервер[с командой Get-транспортсервер](using-the-get-transportserver-command.md)
[: Set-транспортсервер](subcommand-set-transportserver.md)
подкоманда:[Start-транспортсервер](subcommand-start-transportserver.md)
[подкоманда: Get-транспортсервер](subcommand-stop-transportserver.md)
