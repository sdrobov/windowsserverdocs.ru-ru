---
title: Подкоманда Start-Мултикасттрансмиссион
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1b2d459-1ece-49d4-997c-9d206c463b61
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c0e05a1d625e560d85f0af6ae1d76ef8116ddfd8
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383829"
---
# <a name="subcommand-start-multicasttransmission"></a>Подкоманда: Start-Мултикасттрансмиссион

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

запускает пересылку образа по расписанию.
## <a name="syntax"></a>Синтаксис
**Windows Server 2008**
```
wdsutil /start-MulticastTransmissiomedia:<Image name> [/Server:<Server namemediatype:InstallmediaGroup:<Image group name>] [/Filename:<File name>]
```
**Windows Server 2008 R2** для загрузочных образов:
```
wdsutil [Options] /start-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Boot
        /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```
для образов установки:
```
wdsutil [Options] /start-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Install
       mediaGroup:<Image Group>]
        [/Filename:<File name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носитель: <Image name>|Указывает имя изображения.|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: {Загрузка&#124;установки}|Указывает тип изображения. Обратите внимание, что этот параметр должен быть установлен для **установки** для Windows Server 2008.|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Архитектура загрузочного образа, связанного с передачей для запуска. Так как для образов загрузки можно использовать одно и то же имя образа в разных архитектурах, следует указать архитектуру, чтобы гарантировать использование правильной передачи.|
|\Медиаграуп: <Image group name>]|Задает группу образов для образа. Если имя группы образов не указано и на сервере существует только одна группа образов, будет использоваться эта группа образов. Если на сервере существует несколько групп образов, необходимо использовать этот параметр, чтобы указать имя группы образов.|
|[/Филенаме: <File name>]|Указывает имя файла, содержащего образ. Если образ не может быть однозначно идентифицирован по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
## <a name="BKMK_examples"></a>Примеров
Чтобы начать многоадресную передачу, введите одно из следующих действий:
```
wdsutil /start-MulticastTransmissiomedia:"Vista with Office"
/Imagetype:Install
wdsutil /start-MulticastTransmission /Server:MyWDSServemedia:"Vista with Officemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim
```
Чтобы запустить многоадресную передачу образа загрузки для Windows Server 2008 R2, введите:
```
wdsutil /start-MulticastTransmission /Server:MyWDSServemedia:"X64 Boot Imagemediatype:Boot /Architecture:x64
/Filename:boot.wim\n\
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды get-аллмултикасттрансмиссионс](using-the-get-allmulticasttransmissions-command.md)
 с помощью команды[Get-мултикасттрансмиссион](using-the-get-multicasttransmission-command.md)
 с помощью[команды New-мултикасттрансмиссион](using-the-new-multicasttransmission-command.md)
[с помощью Команда Remove-Мултикасттрансмиссион](using-the-remove-multicasttransmission-command.md)
