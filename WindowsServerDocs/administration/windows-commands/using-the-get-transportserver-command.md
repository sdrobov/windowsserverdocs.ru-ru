---
title: С помощью команды get-TransportServer
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 08aa1273d09ba92de15e13f7bfcc8283ac2fedb6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817425"
---
# <a name="using-the-get-transportserver-command"></a>С помощью команды get-TransportServer

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения об указанной транспортного сервера.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-TransportServer [/Server:<Server name>] /Show:{Config}
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|/ Показать: {Config}|Возвращает сведения о указанный транспортный сервер конфигурации.|
## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть сведения о сервере, введите следующую команду:
```
wdsutil /Get-TransportServer /Show:Config
```
Чтобы просмотреть сведения о конфигурации, введите следующую команду:
```
wdsutil /Get-TransportServer /Server:MyWDSServer /Show:Config
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды disable-TransportServer](using-the-disable-transportserver-command.md)
[с помощью команды enable-TransportServer](using-the-enable-transportserver-command.md) 
 [ Подкоманда: set-TransportServer](subcommand-set-transportserver.md)
[подкоманда: start-TransportServer](subcommand-start-transportserver.md)
[подкоманда: stop-TransportServer](subcommand-stop-transportserver.md)
