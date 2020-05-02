---
title: отмена инициализации сервера
description: Справочный раздел, посвященный отмене инициализации — серверу, который возвращает изменения, внесенные в сервер во время первоначальной настройки сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 015efb04-fe84-469f-bd81-49d0046296b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4d7747a44172b7382bd22a7d48ccc717a89ccacb
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721388"
---
# <a name="uninitialize-server"></a>отмена инициализации сервера

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Возвращает изменения, внесенные в сервер во время первоначальной настройки сервера. К ним относятся изменения, внесенные с помощью параметра **/инитиализе-сервер** или оснастки MMC служб развертывания Windows. Обратите внимание, что эта команда сбрасывает сервер в ненастроенное состояние. Эта команда не изменяет содержимое общей папки remoteInstall. Вместо этого он сбрасывает состояние сервера, чтобы можно было повторно инициализировать сервер.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Uninitialize-Server [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a>Примеры
Чтобы повторно инициализировать сервер, введите одно из следующих действий:
```
wdsutil /Uninitialize-Server
wdsutil /verbose /Uninitialize-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Синтаксис](command-line-syntax-key.md)
командной строки[с помощью](using-the-disable-server-command.md)
команды "Disable-Server" с помощью команды "Enable-Server" с помощью команды "[включить](using-the-enable-server-command.md)
[Using the get-Server Command](using-the-get-server-command.md)
сервер" с командой "инициализировать-Server" с помощью подкоманды "[выполнить](subcommand-start-server.md)
[Subcommand: stop-Server](subcommand-stop-server.md) [инициализацию](using-the-initialize-server-command.md)
сервера"[: команда Set-Server](subcommand-set-server.md)
: "
