---
title: Подкоманда Start-Server
description: Раздел команд Windows для команды Start-Server, запускающей все службы для сервера служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1e4343e2-0a16-4e65-8769-c09adaef5680
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bc3e0d11348dd6b531671e62139f2ce2c884c5ee
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833747"
---
# <a name="subcommand-start-server"></a>Подкоманда: Start-Server

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запускает все службы для сервера служб развертывания Windows.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /start-Server [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера для запуска. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы запустить сервер, введите одно из следующих действий:
```
wdsutil /start-Server
wdsutil /verbose /start-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды disable-](using-the-disable-server-command.md) Server
[с помощью команды Enable](using-the-enable-server-command.md) -Server
[с помощью команды Get](using-the-get-server-command.md) -Server,
[с помощью команд Initialize-Server](using-the-initialize-server-command.md) [
подкоманды](the-uninitialize-server-option.md) [: Set-](subcommand-set-server.md) Server [.](subcommand-stop-server.md)


