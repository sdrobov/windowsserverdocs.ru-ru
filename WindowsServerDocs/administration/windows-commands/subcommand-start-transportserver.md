---
title: Подкоманды start-TransportServer
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 5fdfea020019a45eceac0142160f9d5d4d97b989
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59848635"
---
# <a name="subcommand-start-transportserver"></a>Подкоманда: start-TransportServer

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

запускает все службы для транспортного сервера.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /start-TransportServer [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Задает имя используемого транспортного сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеры
Чтобы запустить сервер, введите одно из следующих:
```
wdsutil /start-TransportServer
wdsutil /verbose /start-TransportServer /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды disable-TransportServer](using-the-disable-transportserver-command.md)
[с помощью команды enable-TransportServer](using-the-enable-transportserver-command.md) 
 [ С помощью команды get-TransportServer](using-the-get-transportserver-command.md)
[подкоманда: set-TransportServer](subcommand-set-transportserver.md)
[подкоманда: stop-TransportServer](subcommand-stop-transportserver.md)
