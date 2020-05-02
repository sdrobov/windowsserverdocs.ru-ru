---
title: Get-Мултикасттрансмиссион
description: Справочный раздел по Get-Мултикасттрансмиссион, который отображает сведения об многоадресной передаче для указанного образа.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b733737b-1e81-43d4-a058-d6985a613bef
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a848a4aceb41b4da679d9182459df29c89008fea
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719759"
---
# <a name="get-multicasttransmission"></a>Get-Мултикасттрансмиссион

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о передаче многоадресной рассылки для указанного образа.

## <a name="syntax"></a>Синтаксис
**Windows Server 2008**
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image group name>] 
[/Filename:<File name>] [/Show:Clients]
```
**Windows Server 2008 R2** для передачи загрузочных образов:
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name>
    [/Server:<Server name>]
    [/details:Clients]
  mediatype:Boot
    /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```
для передачи образов установки:
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name>
         [/Server:<Server name>]
         [/details:Clients]
       mediatype:Install
    mediaGroup:<Image Group>]
     [/Filename:<File name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носител<Image name>|Отображает многоадресную передачу, связанную с этим образом.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.|
mediaType: Установка|Указывает тип изображения. Обратите внимание, что этот параметр должен быть установлен в значение **Install**.|
|\Медиаграуп:<Image group name>]|Указывает группу образов, содержащую образ. Если имя группы образов не указано и на сервере существует только одна группа образов, используется эта группа образов. Если на сервере существует несколько групп образов, необходимо использовать этот параметр, чтобы указать группу образов.|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Указывает архитектуру загрузочного образа, связанного с передачей. Так как для образов загрузки можно использовать одно и то же имя образа в разных архитектурах, следует указать архитектуру, чтобы гарантировать использование правильного образа.|
|[/Филенаме:<File name>]|Указывает файл, содержащий изображение. Если образ не может быть однозначно идентифицирован по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|[/Show: Clients]<p>or<p>[/детаилс: клиенты]|Отображает сведения о клиентских компьютерах, подключенных к многоадресной передаче.|
## <a name="examples"></a>Примеры
**Windows Server 2008** Чтобы просмотреть сведения о передаче образа под названием Vista с Office, введите одно из следующих действий:
```
wdsutil /Get-MulticastTransmissiomedia:Vista with Officemediatype:Install
wdsutil /Get-MulticastTransmission /Server:MyWDSServemedia:Vista with Officemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim /Show:Clients
```
**Windows Server 2008 R2** Чтобы просмотреть сведения о передаче образа под названием Vista с Office, введите одно из следующих действий:
```
wdsutil /Get-MulticastTransmissiomedia:Vista with Office
 /Imagetype:Install
```
```
wdsutil /Get-MulticastTransmission /Server:MyWDSServemedia:Vista with Officemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim /details:Clients
```
```
wdsutil /Get-MulticastTransmission /Server:MyWDSServemedia:X64 Boot Imagemediatype:Boot /Architecture:x64 /Filename:boot.wim /details:Clients
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ](command-line-syntax-key.md)
синтаксиса командной строки[с помощью команды](using-the-get-allmulticasttransmissions-command.md)
Get-аллмултикасттрансмиссионс с помощью команды[New-мултикасттрансмиссион](using-the-new-multicasttransmission-command.md)
[с командой Remove-мултикасттрансмиссион](using-the-remove-multicasttransmission-command.md)
[: Start-мултикасттрансмиссион](subcommand-start-multicasttransmission.md)
