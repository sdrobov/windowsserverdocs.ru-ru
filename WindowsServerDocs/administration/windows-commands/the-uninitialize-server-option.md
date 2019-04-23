---
title: Параметр uninitialize сервера
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 015efb04-fe84-469f-bd81-49d0046296b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 73f1ff67331ae41fa0d88cb3a16df5095e0b6d66
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873985"
---
# <a name="the-uninitialize-server-option"></a>Параметр uninitialize сервера

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отменяет изменения, внесенные на сервер во время начальной настройки сервера. Сюда входят изменения, внесенные одним **/initialize-server** параметр или оснастки mmc служб развертывания Windows. Обратите внимание на то, что эта команда сбрасывает сервер в исходное состояние. Эта команда не изменяет содержимое общей папки remoteInstall. Вместо этого он сбрасывает состояние сервера, таким образом, можно повторно инициализировать сервер.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Uninitialize-Server [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеры
Чтобы повторно инициализировать сервер, введите одно из следующих:
```
wdsutil /Uninitialize-Server
wdsutil /verbose /Uninitialize-Server /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды отключения сервера](using-the-disable-server-command.md)
[с помощью команды enable-Server](using-the-enable-server-command.md)
[Using Команда Get-Server](using-the-get-server-command.md)
[с помощью команды Initialize-Server](using-the-initialize-server-command.md)
[подкоманда: set-Server](subcommand-set-server.md) 
 [ Подкоманда: start-Server](subcommand-start-server.md)
[подкоманда: stop-Server](subcommand-stop-server.md)
