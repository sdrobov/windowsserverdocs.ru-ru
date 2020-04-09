---
title: Enable-Транспортсервер
description: Команды Windows в разделе Enable-Транспортсервер, который включает все службы для транспортного сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9d79dba1-4b57-4a00-8cba-877e6b8618e6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9ee5f1206633fb47c4a4b066c099fbf9c7020fb6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831487"
---
# <a name="enable-transportserver"></a>Enable-Транспортсервер

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает все службы для транспортного сервера.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Enable-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя транспортного сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя не указано, будет использоваться локальный сервер.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы включить службы на сервере, выполните одно из следующих действий.
```
wdsutil /Enable-TransportServer
wdsutil /verbose /Enable-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды "Disable-Транспортсервер](using-the-disable-transportserver-command.md) "
[с помощью команды Get-транспортсервер](using-the-get-transportserver-command.md)
подкоманды [: Set-транспортсервер](subcommand-set-transportserver.md)
подкоманду: [Start-транспортсервер](subcommand-start-transportserver.md)
[подкоманды: Get-транспортсервер](subcommand-stop-transportserver.md)
