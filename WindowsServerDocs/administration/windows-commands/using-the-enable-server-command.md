---
title: С помощью команды enable сервера
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: fdf03a778a6c646aa79c2f844212b1728c5c73eb
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852725"
---
# <a name="using-the-enable-server-command"></a>С помощью команды enable сервера

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает все службы для служб развертывания Windows.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Enable-Server [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеры
Чтобы включить службы на сервере, выполните одно из следующих:
```
wdsutil /Enable-Server
wdsutil /verbose /Enable-Server /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды отключения сервера](using-the-disable-server-command.md)
[с помощью команды get сервера](using-the-get-server-command.md)
[Using Команды Initialize-Server](using-the-initialize-server-command.md)
[подкоманда: set-Server](subcommand-set-server.md)
[подкоманда: запустить сервер](subcommand-start-server.md) 
 [ Подкоманда: stop-Server](subcommand-stop-server.md)
[параметр uninitialize сервера](the-uninitialize-server-option.md)
