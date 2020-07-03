---
title: Подкоманда Start-Транспортсервер
description: Справочная статья для подкоманды Start-Транспортсервер, которая запускает все службы для транспортного сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0e93bc84-5b9e-4f9d-8cf0-1634417da0f6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2d70b070d11424b31a615cf1a3fd00f3c80b0069
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936922"
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
|[/Server: <Server name> ]|Указывает имя транспортного сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a>Примеры
Чтобы запустить сервер, введите одно из следующих действий:
```
wdsutil /start-TransportServer
wdsutil /verbose /start-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные ссылки
- Ключ синтаксиса [командной строки](command-line-syntax-key.md) 
 [Использование команды](using-the-disable-transportserver-command.md) 
 Disable-транспортсервер [Использование команды](using-the-enable-transportserver-command.md) 
 Enable-транспортсервер [Использование команды](using-the-get-transportserver-command.md) 
 Get-транспортсервер [Подкоманда: Set-транспортсервер](subcommand-set-transportserver.md) 
 [Подкоманда: транспортсервер](subcommand-stop-transportserver.md)
