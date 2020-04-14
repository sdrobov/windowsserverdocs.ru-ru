---
title: Подкоманда Start-Транспортсервер
description: Раздел команд Windows для подкоманды Start-Транспортсервер, которая запускает все службы для транспортного сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0e93bc84-5b9e-4f9d-8cf0-1634417da0f6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c1356d415006324d75783d4e12ad6882d0fcc779
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833757"
---
# <a name="subcommand-start-transportserver"></a>Подкоманда: Start-Транспортсервер

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запускает все службы для транспортного сервера.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /start-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя транспортного сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы запустить сервер, введите одно из следующих действий:
```
wdsutil /start-TransportServer
wdsutil /verbose /start-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды disable-транспортсервер](using-the-disable-transportserver-command.md)
[помощью команды Enable-транспортсервер](using-the-enable-transportserver-command.md) ,
[с помощью команды Get-транспортсервер,](using-the-get-transportserver-command.md)
[подкоманде Set-транспортсервер](subcommand-set-transportserver.md)
[подкоманде:-транспортсервер](subcommand-stop-transportserver.md)
