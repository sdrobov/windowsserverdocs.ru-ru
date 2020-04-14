---
title: Enable-Server
description: Раздел команд Windows для Enable-Server, который включает все службы для служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 939ffbfb-cf3c-4310-9627-6e7e0c0644d6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6b10ff920667cfdbaae5baaf096bf56e11ce880e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831547"
---
# <a name="enable-server"></a>Enable-Server

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает все службы для служб развертывания Windows.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Enable-Server [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы включить службы на сервере, выполните одно из следующих действий.
```
wdsutil /Enable-Server
wdsutil /verbose /Enable-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды "Disable-Server](using-the-disable-server-command.md) "
[с помощью команды Get](using-the-get-server-command.md) -Server,
при [помощи команды "инициализировать-Server Command](using-the-initialize-server-command.md)
": " [Set-](subcommand-set-server.md) Server
подкоманда: [Start-](subcommand-start-server.md) Server
[подкоманде:"-Server](subcommand-stop-server.md)
[параметром "Uninitialize-Server](the-uninitialize-server-option.md) ".
