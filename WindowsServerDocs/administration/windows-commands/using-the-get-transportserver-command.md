---
title: Get-Транспортсервер
description: Раздел команд Windows для Get-Транспортсервер, который отображает сведения о указанном транспортном сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: de634123-0179-41b2-9c6f-726508130ff5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 549eb32536bda201a81e5f40ef408359fae39f4b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830817"
---
# <a name="get-transportserver"></a>Get-Транспортсервер

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о указанном транспортном сервере.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-TransportServer [/Server:<Server name>] /Show:{Config}
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Show: {config}|Возвращает сведения о конфигурации указанного транспортного сервера.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы просмотреть сведения о сервере, введите:
```
wdsutil /Get-TransportServer /Show:Config
```
Чтобы просмотреть сведения о конфигурации, введите:
```
wdsutil /Get-TransportServer /Server:MyWDSServer /Show:Config
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды Disable-Транспортсервер](using-the-disable-transportserver-command.md) ,
[с помощью команды Enable-транспортсервер](using-the-enable-transportserver-command.md)
подкоманде [: Set-транспортсервер](subcommand-set-transportserver.md)
подкоманде: [Start-транспортсервер](subcommand-start-transportserver.md)
[подкоманды:-транспортсервер](subcommand-stop-transportserver.md)
