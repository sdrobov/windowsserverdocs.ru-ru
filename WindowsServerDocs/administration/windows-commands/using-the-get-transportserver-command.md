---
title: Использование команды Get-Транспортсервер
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de634123-0179-41b2-9c6f-726508130ff5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 282b69162cf3550c5bcba3282b60f15072c96ed6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363071"
---
# <a name="using-the-get-transportserver-command"></a>Использование команды Get-Транспортсервер

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о указанном транспортном сервере.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-TransportServer [/Server:<Server name>] /Show:{Config}
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Show: {config}|Возвращает сведения о конфигурации указанного транспортного сервера.|
## <a name="BKMK_examples"></a>Примеров
Чтобы просмотреть сведения о сервере, введите:
```
wdsutil /Get-TransportServer /Show:Config
```
Чтобы просмотреть сведения о конфигурации, введите:
```
wdsutil /Get-TransportServer /Server:MyWDSServer /Show:Config
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксис командной строки](command-line-syntax-key.md)
[с помощью команды disable-транспортсервер](using-the-disable-transportserver-command.md)
[с помощью команды Enable-транспортсервер](using-the-enable-transportserver-command.md)
 подкоманда[: Set-транспортсервер](subcommand-set-transportserver.md)
[подкоманда: подкоманда Start-Транспортсервер](subcommand-start-transportserver.md)
[: останавливается-транспортсервер](subcommand-stop-transportserver.md)
