---
title: Подкоманды stop-Server
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09f411c0-099f-4591-95fd-b77b3fd9118a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ddb681234cfcbe6d02e56f2e366167faeeb25280
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59834735"
---
# <a name="subcommand-stop-server"></a>Подкоманда: stop-Server

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Останавливает все службы на сервере служб развертывания Windows.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Stop-Server [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеры
Чтобы остановить службы, введите одно из следующих:
```
wdsutil /Stop-Server
wdsutil /verbose /Stop-Server /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды отключения сервера](using-the-disable-server-command.md)
[с помощью команды enable-Server](using-the-enable-server-command.md)
[Using Команда Get-Server](using-the-get-server-command.md)
[с помощью команды Initialize-Server](using-the-initialize-server-command.md)
[подкоманда: set-Server](subcommand-set-server.md) 
 [ Подкоманда: start-Server](subcommand-start-server.md)
[параметр uninitialize сервера](the-uninitialize-server-option.md)
