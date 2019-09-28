---
title: Использование команды Initialize-Server
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: b9e95972838fc70ee1e617d1e299c9e35db5b979
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392096"
---
# <a name="using-the-initialize-server-command"></a>Использование команды Initialize-Server

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Настраивает сервер служб развертывания Windows для первоначального использования после установки роли сервера. После выполнения этой команды следует использовать команду [Add-Image](using-the-add-image-command.md) , чтобы добавить образы на сервер.
## <a name="syntax"></a>Синтаксис
```
wdsutil /Initialize-Server [/Server:<Server name>] /remInst:<Full path> [/Authorize]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Реминст: "<Full path>"|Указывает полный путь и имя папки remoteInstall. Если указанная папка еще не существует, этот параметр будет создан при выполнении команды. Всегда следует вводить локальный путь даже в случае удаленного компьютера. Пример: **Д:\ремотеинсталл**.|
|/Authorize|Авторизация сервера в протоколе DHCP. Этот параметр необходим только в том случае, если включено обнаружение мошеннических DHCP-серверов, что означает, что сервер PXE служб развертывания Windows должен быть авторизован в службе DHCP перед обслуживанием клиентских компьютеров. Обратите внимание, что обнаружение случайного DHCP-сервера отключено по умолчанию.|
## <a name="BKMK_examples"></a>Примеров
Чтобы инициализировать сервер и установить общую папку remoteInstall на диск F:, введите.
```
wdsutil /Initialize-Server /remInst:"F:\remoteInstall"
```
Чтобы инициализировать сервер и задать для общей папки remoteInstall диск C:, введите.
```
wdsutil /verbose /Progress /Initialize-Server /Server:MyWDSServer /remInst:"C:\remoteInstall"
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксис командной строки](command-line-syntax-key.md)
[с помощью команды disable-Server](using-the-disable-server-command.md)
[с помощью команды Enable-](using-the-enable-server-command.md)Server 
 с[помощью команды Get](using-the-get-server-command.md)-server 
[: Set-Server](subcommand-set-server.md)@no__t[-9 подкоманда: подкоманда Start-Server](subcommand-start-server.md)1: @no__t-[Server](subcommand-stop-server.md)-13[параметр Uninitialize-Server](the-uninitialize-server-option.md)
