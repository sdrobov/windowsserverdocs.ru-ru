---
title: Подкоманда Start-Server
description: Справочный раздел для команды Start-Server, запускающей все службы для сервера служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1e4343e2-0a16-4e65-8769-c09adaef5680
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e2a6de007e62bf3be5544f97b53a4fcc13118985
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721651"
---
# <a name="subcommand-start-server"></a>Подкоманда: Start-Server

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запускает все службы для сервера служб развертывания Windows.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /start-Server [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера для запуска. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a>Примеры
Чтобы запустить сервер, введите одно из следующих действий:
```
wdsutil /start-Server
wdsutil /verbose /start-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Синтаксис](command-line-syntax-key.md)
командной строки[с помощью](using-the-disable-server-command.md)
команды "Disable-Server" с помощью команды "Enable-Server" с помощью команды "[включить](using-the-enable-server-command.md)
[Using the get-Server Command](using-the-get-server-command.md)
сервер" с командой "инициализировать-Server" с помощью подкоманды "выполнить[инициализацию](using-the-initialize-server-command.md)
сервера": "команда[Set-Server](subcommand-set-server.md)
[Subcommand: stop-Server](subcommand-stop-server.md)
["](the-uninitialize-server-option.md) .
