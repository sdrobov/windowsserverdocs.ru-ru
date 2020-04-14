---
title: Disable-Транспортсервер
description: Команды Windows в разделе Disable-Транспортсервер, который отключает все службы для транспортного сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a009706b-8e89-486b-8e3d-512cd9f4de74
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 39f930a464364cda680098ef4e7e1081d0995503
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831627"
---
# <a name="disable-transportserver"></a>Disable-Транспортсервер

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отключает все службы для транспортного сервера.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Disable-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя транспортного сервера, который должен быть отключен. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя транспортного сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы отключить сервер, введите:
```
wdsutil /Disable-TransportServer
wdsutil /verbose /Disable-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[помощью команды Enable-Транспортсервер,](using-the-enable-transportserver-command.md)
[с помощью команды Get-транспортсервер](using-the-get-transportserver-command.md)
подкоманды [: Set-Транспортсервер](subcommand-set-transportserver.md)
подкоманда: [Start-транспортсервер](subcommand-start-transportserver.md)
[подкоманды: Get-транспортсервер](subcommand-stop-transportserver.md)
