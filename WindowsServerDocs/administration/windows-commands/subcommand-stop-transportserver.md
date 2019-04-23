---
title: Подкоманды stop-TransportServer
description: Раздел Windows команды stop-TransportServer
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 8f7410a8720337e509325b99863446bd8d19eb26
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59853455"
---
# <a name="subcommand-stop-transportserver"></a>Подкоманда: stop-TransportServer

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Останавливает все службы на транспортном сервере.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Stop-TransportServer [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Задает имя используемого транспортного сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если сервер транспорта не указан, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеры
Чтобы остановить службы, введите одно из следующих:
```
wdsutil /Stop-TransportServer
wdsutil /verbose /Stop-TransportServer /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды disable-TransportServer](using-the-disable-transportserver-command.md)
[с помощью команды enable-TransportServer](using-the-enable-transportserver-command.md) 
 [ С помощью команды get-TransportServer](using-the-get-transportserver-command.md)
[подкоманда: set-TransportServer](subcommand-set-transportserver.md)
[подкоманда: start-TransportServer](subcommand-start-transportserver.md)
