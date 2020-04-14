---
title: Initialize-Server
description: Раздел команд Windows для команды Initialize-Server, который настраивает сервер служб развертывания Windows для первоначального использования после установки роли сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 68a26ad9-5eb2-4490-b782-b7cd46b8000d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2c80af07827c889a3dd1c5d3050cd2ca3b4c8f1e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830797"
---
# <a name="initialize-server"></a>Initialize-Server

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы инициализировать сервер и установить общую папку remoteInstall на диск F:, введите.
```
wdsutil /Initialize-Server /remInst:F:\remoteInstall
```
Чтобы инициализировать сервер и задать для общей папки remoteInstall диск C:, введите.
```
wdsutil /verbose /Progress /Initialize-Server /Server:MyWDSServer /remInst:C:\remoteInstall
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды disable-](using-the-disable-server-command.md) Server
[с помощью команды Enable](using-the-enable-server-command.md) -Server
[с помощью](using-the-get-server-command.md) команды
Get-Server
подкоманды: [Set-Server](subcommand-set-server.md) подкоманда: [Start-Server](subcommand-start-server.md)
[подкоманда:-Server](subcommand-stop-server.md)
[параметром Uninitialize-Server](the-uninitialize-server-option.md)
