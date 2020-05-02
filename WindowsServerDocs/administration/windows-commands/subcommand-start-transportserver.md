---
title: Подкоманда Start-Транспортсервер
description: Справочный раздел для подкоманды Start-Транспортсервер, которая запускает все службы для транспортного сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0e93bc84-5b9e-4f9d-8cf0-1634417da0f6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 92bd68421883c49ec29dfb78f06121bff880b01e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721637"
---
# <a name="subcommand-start-transportserver"></a>Подкоманда: Start-Транспортсервер

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запускает все службы для транспортного сервера.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /start-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя транспортного сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a>Примеры
Чтобы запустить сервер, введите одно из следующих действий:
```
wdsutil /start-TransportServer
wdsutil /verbose /start-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ](command-line-syntax-key.md)
синтаксиса командной строки[с помощью команды Disable-транспортсервер](using-the-disable-transportserver-command.md)
с командой[Enable-транспортсервер](using-the-enable-transportserver-command.md)
[с использованием подкоманды Get-транспортсервер](using-the-get-transportserver-command.md)
с помощью команды[Set-транспортсервер](subcommand-set-transportserver.md)
[: "-транспортсервер".](subcommand-stop-transportserver.md)
