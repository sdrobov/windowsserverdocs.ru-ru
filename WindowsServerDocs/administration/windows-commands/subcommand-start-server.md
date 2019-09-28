---
title: Подкоманда Start-Server
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1e4343e2-0a16-4e65-8769-c09adaef5680
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 78407f3474c48b928535abb652d2c023dd1c1c14
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383819"
---
# <a name="subcommand-start-server"></a>Подкоманда: Start-Server

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

запускает все службы для сервера служб развертывания Windows.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /start-Server [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя сервера для запуска. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеров
Чтобы запустить сервер, введите одно из следующих действий:
```
wdsutil /start-Server
wdsutil /verbose /start-Server /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксис командной строки](command-line-syntax-key.md)
[с помощью команды disable-Server](using-the-disable-server-command.md)
 с[помощью команды Enable-](using-the-enable-server-command.md)Server 
 с помощью команды[Get](using-the-get-server-command.md)-Server 
[с помощью команды Initialize-Server](using-the-initialize-server-command.md)
[ . Подкоманда: Set-Server](subcommand-set-server.md)1,[подкоманда:](subcommand-stop-server.md)@no__t-Server-13[параметр Uninitialize-Server](the-uninitialize-server-option.md)
