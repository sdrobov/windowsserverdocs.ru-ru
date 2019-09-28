---
title: Подкоманда-Транспортсервер
description: Раздел команд Windows для команды "Транспортсервер"
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc1b1eec-6893-445e-81dc-16b3fae287fa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2a2444328a426429c2dce5ceee3272cf1dc814cc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370724"
---
# <a name="subcommand-stop-transportserver"></a>Подкоманда: Транспортсервер

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Останавливает все службы на транспортном сервере.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Stop-TransportServer [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя транспортного сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если транспортный сервер не указан, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеров
Чтобы отключить службы, введите одно из следующих действий.
```
wdsutil /Stop-TransportServer
wdsutil /verbose /Stop-TransportServer /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды disable-транспортсервер](using-the-disable-transportserver-command.md)
[с помощью команды Enable-Транспортсервер](using-the-enable-transportserver-command.md)
[с помощью команды Get-транспортсервер](using-the-get-transportserver-command.md)
[. команда Set-Транспортсервер](subcommand-set-transportserver.md)
[: Start-транспортсервер](subcommand-start-transportserver.md)
