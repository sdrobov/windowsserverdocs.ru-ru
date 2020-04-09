---
title: отмена инициализации сервера
description: Команды Windows для отмены инициализации — сервера, которые отменяют изменения, внесенные в сервер во время первоначальной настройки сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 015efb04-fe84-469f-bd81-49d0046296b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4ed912af1ec3bc505e1e7465650a119af979b407
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833117"
---
# <a name="uninitialize-server"></a>отмена инициализации сервера

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Возвращает изменения, внесенные в сервер во время первоначальной настройки сервера. К ним относятся изменения, внесенные с помощью параметра **/инитиализе-сервер** или оснастки MMC служб развертывания Windows. Обратите внимание, что эта команда сбрасывает сервер в ненастроенное состояние. Эта команда не изменяет содержимое общей папки remoteInstall. Вместо этого он сбрасывает состояние сервера, чтобы можно было повторно инициализировать сервер.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Uninitialize-Server [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы повторно инициализировать сервер, введите одно из следующих действий:
```
wdsutil /Uninitialize-Server
wdsutil /verbose /Uninitialize-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды disable-](using-the-disable-server-command.md) Server
[с помощью команды Enable](using-the-enable-server-command.md) -Server
[с помощью команды Get](using-the-get-server-command.md) -Server,
[с помощью команд Initialize-Server](using-the-initialize-server-command.md)
подкоманды: [Set-](subcommand-set-server.md) Server подкоманда: [Start](subcommand-start-server.md) -Server [
.](subcommand-stop-server.md)

