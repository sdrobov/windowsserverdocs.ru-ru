---
title: Подкоманда Start-Транспортсервер
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e93bc84-5b9e-4f9d-8cf0-1634417da0f6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c1bdf80aa9c255e12e1e4821467d556eb67f8691
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370732"
---
# <a name="subcommand-start-transportserver"></a>Подкоманда: Start-Транспортсервер

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

запускает все службы для транспортного сервера.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /start-TransportServer [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя транспортного сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеров
Чтобы запустить сервер, введите одно из следующих действий:
```
wdsutil /start-TransportServer
wdsutil /verbose /start-TransportServer /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды disable-транспортсервер](using-the-disable-transportserver-command.md)
[с помощью команды Enable-Транспортсервер](using-the-enable-transportserver-command.md)
[с помощью команды Get-транспортсервер](using-the-get-transportserver-command.md)
[. подкоманда Set-Транспортсервер](subcommand-set-transportserver.md)
[:-транспортсервер](subcommand-stop-transportserver.md)
