---
title: Использование команды Disable-Транспортсервер
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a009706b-8e89-486b-8e3d-512cd9f4de74
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7531f8a638ac8fabdad08cc0134dbc63873505de
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363456"
---
# <a name="using-the-disable-transportserver-command"></a>Использование команды Disable-Транспортсервер

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отключает все службы для транспортного сервера.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Disable-TransportServer [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя транспортного сервера, который должен быть отключен. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя транспортного сервера не указано, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеров
Чтобы отключить сервер, введите:
```
wdsutil /Disable-TransportServer
wdsutil /verbose /Disable-TransportServer /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды enable-транспортсервер](using-the-enable-transportserver-command.md)
[с помощью команды Get-транспортсервер](using-the-get-transportserver-command.md)
 подкоманды[Set-транспортсервер](subcommand-set-transportserver.md)@no__t[-7: подкоманда Start-Транспортсервер](subcommand-start-transportserver.md)
[: останавливается-транспортсервер](subcommand-stop-transportserver.md)
