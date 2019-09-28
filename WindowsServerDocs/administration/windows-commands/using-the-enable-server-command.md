---
title: Использование команды Enable-Server
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 939ffbfb-cf3c-4310-9627-6e7e0c0644d6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0b90621ec14c6cf451d7a05eace79f2e0679b2f4
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363452"
---
# <a name="using-the-enable-server-command"></a>Использование команды Enable-Server

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает все службы для служб развертывания Windows.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Enable-Server [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеров
Чтобы включить службы на сервере, выполните одно из следующих действий.
```
wdsutil /Enable-Server
wdsutil /verbose /Enable-Server /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксис командной строки](command-line-syntax-key.md)
[с помощью команды "отключить сервер](using-the-disable-server-command.md)" 
 с[помощью команды Get](using-the-get-server-command.md)-Server 
 с[помощью команды Initialize-Server](using-the-initialize-server-command.md)
[: Set-Server](subcommand-set-server.md)
[ Подкоманда: Start-Server](subcommand-start-server.md)1[подкоманда:-Server](subcommand-stop-server.md)3[параметр Uninitialize-Server](the-uninitialize-server-option.md)
