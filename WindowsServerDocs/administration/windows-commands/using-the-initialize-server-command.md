---
title: Initialize-Server
description: Справочный раздел по Initialize-Server, который настраивает сервер служб развертывания Windows для первоначального использования после установки роли сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 68a26ad9-5eb2-4490-b782-b7cd46b8000d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 54180923a077c0b423e73588bcbd1c03b0154d08
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719718"
---
# <a name="initialize-server"></a>Initialize-Server

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Настраивает сервер служб развертывания Windows для первоначального использования после установки роли сервера. После выполнения этой команды следует использовать команду [Add-Image](using-the-add-image-command.md) , чтобы добавить образы на сервер.
## <a name="syntax"></a>Синтаксис
```
wdsutil /Initialize-Server [/Server:<Server name>] /remInst:<Full path> [/Authorize]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Реминст:<Full path>|Указывает полный путь и имя папки remoteInstall. Если указанная папка еще не существует, этот параметр будет создан при выполнении команды. Всегда следует вводить локальный путь даже в случае удаленного компьютера. Например: **д:\ремотеинсталл**.|
|/Authorize|Авторизация сервера в протоколе DHCP. Этот параметр необходим только в том случае, если включено обнаружение мошеннических DHCP-серверов, что означает, что сервер PXE служб развертывания Windows должен быть авторизован в службе DHCP перед обслуживанием клиентских компьютеров. Обратите внимание, что обнаружение случайного DHCP-сервера отключено по умолчанию.|
## <a name="examples"></a>Примеры
Чтобы инициализировать сервер и установить общую папку remoteInstall на диск F:, введите.
```
wdsutil /Initialize-Server /remInst:F:\remoteInstall
```
Чтобы инициализировать сервер и задать для общей папки remoteInstall диск C:, введите.
```
wdsutil /verbose /Progress /Initialize-Server /Server:MyWDSServer /remInst:C:\remoteInstall
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Синтаксис](command-line-syntax-key.md)
командной строки[с помощью команды "Disable-](using-the-disable-server-command.md)
Server" с помощью команды "[Enable](using-the-enable-server-command.md)
-Server" с использованием подкоманды[Get](using-the-get-server-command.md)
-Server[: Set-Server](subcommand-set-server.md)
подкоманда:[Start-Server](subcommand-start-server.md)
подкоманда[: "-Server](subcommand-stop-server.md)
[", параметр отмены инициализации сервера](the-uninitialize-server-option.md)
