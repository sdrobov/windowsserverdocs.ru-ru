---
title: С помощью команды enable-TransportServer
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 40793ac0b9dc7d8b4a80d6a66b55244202aa37d1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59834335"
---
# <a name="using-the-enable-transportserver-command"></a>С помощью команды enable-TransportServer

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает все службы для транспортного сервера.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Enable-TransportServer [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Задает имя используемого транспортного сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя не указано, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеры
Чтобы включить службы на сервере, выполните одно из следующих:
```
wdsutil /Enable-TransportServer
wdsutil /verbose /Enable-TransportServer /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды disable-TransportServer](using-the-disable-transportserver-command.md)
[с помощью команды get-TransportServer](using-the-get-transportserver-command.md) 
 [Подкоманда: set-TransportServer](subcommand-set-transportserver.md)
[подкоманда: start-TransportServer](subcommand-start-transportserver.md)
[подкоманда: stop-TransportServer](subcommand-stop-transportserver.md)
