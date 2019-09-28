---
title: Использование команды Enable-Транспортсервер
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9d79dba1-4b57-4a00-8cba-877e6b8618e6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 732a021b02193a3bfb5cb573a33879dbecb840b9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363433"
---
# <a name="using-the-enable-transportserver-command"></a>Использование команды Enable-Транспортсервер

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает все службы для транспортного сервера.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Enable-TransportServer [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя транспортного сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя не указано, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеров
Чтобы включить службы на сервере, выполните одно из следующих действий.
```
wdsutil /Enable-TransportServer
wdsutil /verbose /Enable-TransportServer /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксис командной строки](command-line-syntax-key.md)
[с помощью команды disable-транспортсервер](using-the-disable-transportserver-command.md)
[с помощью команды Get-транспортсервер](using-the-get-transportserver-command.md)
 подкоманды[Set-транспортсервер](subcommand-set-transportserver.md)@no__t[-7: подкоманда Start-Транспортсервер](subcommand-start-transportserver.md)
[: останавливается-транспортсервер](subcommand-stop-transportserver.md)
