---
title: Подкоманда-сервер
description: Справочный раздел для подкоманды Stop-Server, которая останавливает все службы на сервере служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 09f411c0-099f-4591-95fd-b77b3fd9118a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 68cc73ac016e2ffded774567034801e1c11944d1
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721634"
---
# <a name="subcommand-stop-server"></a>Подкоманда:-сервер

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Останавливает все службы на сервере служб развертывания Windows.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Stop-Server [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a>Примеры
Чтобы отключить службы, введите одно из следующих действий.
```
wdsutil /Stop-Server
wdsutil /verbose /Stop-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Синтаксис](command-line-syntax-key.md)
командной строки[с помощью](using-the-disable-server-command.md)
команды "Disable-Server" с помощью команды "Enable-Server" с помощью команды "[включить](using-the-enable-server-command.md)
[Using the get-Server Command](using-the-get-server-command.md)
сервер" с командой "инициализировать-Server" с помощью[подкоманды](subcommand-set-server.md)
["выполнить инициализацию](using-the-initialize-server-command.md)
сервера": "[Start-](subcommand-start-server.md)
Server["](the-uninitialize-server-option.md) .
