---
title: С помощью команды Initialize-Server
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68a26ad9-5eb2-4490-b782-b7cd46b8000d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a1f3a1c02eb21f630aaff7219610864cd1db2a7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825195"
---
# <a name="using-the-initialize-server-command"></a>С помощью команды Initialize-Server

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Настройка сервера служб развертывания Windows для первого использования после установки роли сервера. После выполнения этой команды следует использовать [с помощью команды add образа](using-the-add-image-command.md) команду, чтобы добавить образы на сервер.
## <a name="syntax"></a>Синтаксис
```
wdsutil /Initialize-Server [/Server:<Server name>] /remInst:<Full path> [/Authorize]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|/remInst:"<Full path>"|Указывает полный путь и имя папки remoteInstall. Если указанная папка не существует, этот параметр создаст ее, когда выполняется команда. Всегда следует ввести локальный путь, даже в случае удаленного компьютера. Пример: **D:\remoteInstall**.|
|[/ Authorize]|Дает возможность серверу в элемент управления протокола DHCP (Dynamic Host). Данный параметр является обязательным только в том случае, если включено обнаружение посторонних подключений DHCP, это означает, что PXE служб развертывания Windows server должны быть авторизованы в DHCP до клиентских компьютеров. Обратите внимание, что обнаружение посторонних подключений DHCP отключен по умолчанию.|
## <a name="BKMK_examples"></a>Примеры
Для инициализации сервера, а значение общей папке remoteInstall диска «f:», введите следующую команду.
```
wdsutil /Initialize-Server /remInst:"F:\remoteInstall"
```
Инициализировать сервера и общей папке remoteInstall к диску C:, введите следующую команду.
```
wdsutil /verbose /Progress /Initialize-Server /Server:MyWDSServer /remInst:"C:\remoteInstall"
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды отключения сервера](using-the-disable-server-command.md)
[с помощью команды enable-Server](using-the-enable-server-command.md)
[Using Команда Get-Server](using-the-get-server-command.md)
[подкоманда: set-Server](subcommand-set-server.md)
[подкоманда: запустить сервер](subcommand-start-server.md)
[подкоманда: STOP-Server](subcommand-stop-server.md)
[параметр uninitialize сервера](the-uninitialize-server-option.md)
