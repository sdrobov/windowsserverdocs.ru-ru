---
title: Используя команду disable-TransportServer
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: d653aacf225333ac8a8b090ef53fb6826e84ab5c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59836985"
---
# <a name="using-the-disable-transportserver-command"></a>Используя команду disable-TransportServer

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отключает все службы для транспортного сервера.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Disable-TransportServer [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Задает имя используемого транспортного сервера должно быть отключено. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя транспортного сервера не указано, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеры
Чтобы отключить сервер, введите следующую команду:
```
wdsutil /Disable-TransportServer
wdsutil /verbose /Disable-TransportServer /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды enable-TransportServer](using-the-enable-transportserver-command.md)
[с помощью команды get-TransportServer](using-the-get-transportserver-command.md) 
 [Подкоманда: set-TransportServer](subcommand-set-transportserver.md)
[подкоманда: start-TransportServer](subcommand-start-transportserver.md)
[подкоманда: stop-TransportServer](subcommand-stop-transportserver.md)
