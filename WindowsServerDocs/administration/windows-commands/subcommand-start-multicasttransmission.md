---
title: Подкоманда Start-Мултикасттрансмиссион
description: Раздел команд Windows для подкоманды Start-Мултикасттрансмиссион, которая запускает передачу образа по расписанию.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a1b2d459-1ece-49d4-997c-9d206c463b61
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e882c54d2fbe744ca9fe25b2631f4d875886c756
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833787"
---
# <a name="subcommand-start-multicasttransmission"></a>Подкоманда: Start-Мултикасттрансмиссион

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запускает пересылку образа по расписанию.

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
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носитель:<Image name>|Указывает имя образа.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: {Загрузка&#124;установки}|Указывает тип изображения. Обратите внимание, что этот параметр должен быть установлен для **установки** для Windows Server 2008.|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Архитектура загрузочного образа, связанного с передачей для запуска. Так как для образов загрузки можно использовать одно и то же имя образа в разных архитектурах, следует указать архитектуру, чтобы гарантировать использование правильной передачи.|
|\Медиаграуп:<Image group name>]|Задает группу образов для образа. Если имя группы образов не указано и на сервере существует только одна группа образов, будет использоваться эта группа образов. Если на сервере существует несколько групп образов, необходимо использовать этот параметр, чтобы указать имя группы образов.|
|[/Филенаме:<File name>]|Указывает имя файла, содержащего образ. Если образ не может быть однозначно идентифицирован по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы начать многоадресную передачу, введите одно из следующих действий:
```
wdsutil /start-MulticastTransmissiomedia:Vista with Office
/Imagetype:Install
wdsutil /start-MulticastTransmission /Server:MyWDSServemedia:Vista with Officemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim
```
Чтобы запустить многоадресную передачу образа загрузки для Windows Server 2008 R2, введите:
```
wdsutil /start-MulticastTransmission /Server:MyWDSServemedia:X64 Boot Imagemediatype:Boot /Architecture:x64
/Filename:boot.wim\n\
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью](using-the-get-allmulticasttransmissions-command.md) команды get-аллмултикасттрансмиссионс,
[помощью команды Get-мултикасттрансмиссион](using-the-get-multicasttransmission-command.md) ,
с помощью команды [New-мултикасттрансмиссион,](using-the-new-multicasttransmission-command.md)
[с помощью команды Remove-мултикасттрансмиссион](using-the-remove-multicasttransmission-command.md) .
