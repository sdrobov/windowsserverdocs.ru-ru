---
title: Подкоманда-сервер
description: Раздел команд Windows для подкоманды Stop-Server, которая останавливает все службы на сервере служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 09f411c0-099f-4591-95fd-b77b3fd9118a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2671e7a2c2e5bb542cecd9374ad6364d68ff5bd4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833717"
---
# <a name="subcommand-stop-server"></a>Подкоманда:-сервер

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Останавливает все службы на сервере служб развертывания Windows.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Stop-Server [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы отключить службы, введите одно из следующих действий.
```
wdsutil /Stop-Server
wdsutil /verbose /Stop-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды «Disable-](using-the-disable-server-command.md) Server»
[с помощью команды Enable](using-the-enable-server-command.md) -Server
[с помощью команды Get](using-the-get-server-command.md) -Server,
[с помощью команд Initialize-Server](using-the-initialize-server-command.md)
подкоманды [: Set-](subcommand-set-server.md) [сервера
](the-uninitialize-server-option.md) [.](subcommand-start-server.md)

