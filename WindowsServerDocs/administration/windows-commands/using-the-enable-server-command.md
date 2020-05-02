---
title: Enable-Server
description: Справочный раздел по Enable-Server, который включает все службы для служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 939ffbfb-cf3c-4310-9627-6e7e0c0644d6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bf7bf57c0784fa16719b9f77da50212bca0ef850
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720935"
---
# <a name="enable-server"></a>Enable-Server

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает все службы для служб развертывания Windows.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Enable-Server [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a>Примеры
Чтобы включить службы на сервере, выполните одно из следующих действий.
```
wdsutil /Enable-Server
wdsutil /verbose /Enable-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ](command-line-syntax-key.md)
синтаксиса командной строки с использованием команды "[Disable-](using-the-disable-server-command.md)
Server" с помощью команды[Get](using-the-get-server-command.md)
-Server с командой["инициализировать-](using-the-initialize-server-command.md)
Server"[: Set-](subcommand-set-server.md)
Server подкоманда:[Start-](subcommand-start-server.md)
Server подкоманда[: "-Server](subcommand-stop-server.md)
[", параметр отмены инициализации сервера](the-uninitialize-server-option.md)
