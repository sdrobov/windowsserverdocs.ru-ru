---
title: Initialize-Server
description: Справочная статья по Initialize-Server, которая настраивает сервер служб развертывания Windows для первоначального использования после установки роли сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 68a26ad9-5eb2-4490-b782-b7cd46b8000d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 22c93a07e4c2785e8cda497e9698b2031c764a42
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932161"
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
|[/Server: <Server name> ]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
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
- Ключ синтаксиса [командной строки](command-line-syntax-key.md) 
 [Использование команды «Disable-Server»](using-the-disable-server-command.md) 
 [Использование команды](using-the-enable-server-command.md) 
 Enable-Server [Использование команды](using-the-get-server-command.md) 
 Get-Server [Подкоманда: Set-Server](subcommand-set-server.md) 
 [Подкоманда: Start-Server](subcommand-start-server.md) 
 [Подкоманда:-сервер](subcommand-stop-server.md) 
 [Параметр Uninitialize-Server](the-uninitialize-server-option.md)
