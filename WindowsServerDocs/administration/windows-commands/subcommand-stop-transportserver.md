---
title: Подкоманда-Транспортсервер
description: Раздел команд Windows для команды "Транспортсервер"
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: dc1b1eec-6893-445e-81dc-16b3fae287fa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 44d62332307ffda4dcfa6af286c7b95cb12423dc
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833707"
---
# <a name="subcommand-stop-transportserver"></a>Подкоманда: Транспортсервер

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Останавливает все службы на транспортном сервере.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Stop-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя транспортного сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если транспортный сервер не указан, будет использоваться локальный сервер.|
## <a name="examples"></a><a name="BKMK_examples"></a>Примеров
Чтобы отключить службы, введите одно из следующих действий.
```
wdsutil /Stop-TransportServer
wdsutil /verbose /Stop-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды disable-транспортсервер](using-the-disable-transportserver-command.md)
[помощью команды Enable-транспортсервер](using-the-enable-transportserver-command.md) ,
[с помощью команды Get-Транспортсервер](using-the-get-transportserver-command.md)
[подкоманде Set-транспортсервер](subcommand-set-transportserver.md)
[подкоманде: Start-транспортсервер](subcommand-start-transportserver.md)
