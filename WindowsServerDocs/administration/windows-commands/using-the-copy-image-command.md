---
title: Copy-Image
description: Раздел команд Windows для Copy-Image, который копирует образы, которые находятся в одной и той же группе образов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bea41cf4-36e6-4181-afa5-00170ebd4fdc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 443fa5bc87bbc7554e13f4b2a7fb7e36aa43dfaa
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831707"
---
# <a name="copy-image"></a>Copy-Image

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует образы, которые находятся в одной и той же группе образов. Для копирования образов между группами образов используйте команду [Export-Image](using-the-export-image-command.md) , а затем команду [Add-Image](using-the-add-image-command.md) .
Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /copy-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:Install
    mediaGroup:<Image group name>]
     [/Filename:<File name>]
     /DestinationImage
         /Name:<Name>
         /Filename:<File name>
         [/Description:<Description>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носитель:<Image name>|Задает имя копируемого образа.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: Установка|Указывает тип копируемого изображения. Этот параметр должен быть установлен в значение " **установить**".|
|\Медиаграуп:<Image group name>]|Указывает группу образов, содержащую копируемый образ. Если группа образов не указана и на сервере существует только одна группа, то эта группа образов будет использоваться по умолчанию. Если на сервере существует более одной группы образов, необходимо указать группу образов.|
|[/Филенаме:<Filename>]|Указывает имя файла копируемого образа. Если исходный образ не может быть однозначно определен по имени, необходимо указать имя файла.|
|/дестинатионимаже|Задает параметры для конечного образа, как описано в следующей таблице.<p>-/Name:<Name> — задает отображаемое имя копируемого образа.<br />-/Филенаме:<Filename> — задает имя конечного файла образа, который будет содержать копию образа.<br />-[/Description: <Description>] — Задает описание копии образа.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы создать копию указанного образа и назовите ее Виндовсвиста. wim, введите:
```
wdsutil /copy-Imagmedia:Windows Vista with Officemediatype:Install /DestinationImage /Name:copy of Windows Vista with Office /Filename:WindowsVista.wim
```
Чтобы создать копию указанного образа, примените указанные параметры и назовите копию Виндовсвиста. wim, введите:
```
wdsutil /verbose /Progress /copy-Imagmedia:Windows Vista with Office /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:install.wim /DestinationImage /Name:copy of Windows Vista with Office /Filename:WindowsVista.wim /Description:This is a copy of the original Windows image with Office installed
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[Использование команды add-](using-the-add-image-command.md) Image
[помощью команды Export-Image](using-the-export-image-command.md)
помощью команды [Get-](using-the-get-image-command.md) Image
[помощью команды Remove](using-the-remove-image-command.md) -image,
[с помощью команды replace-](using-the-replace-image-command.md) Image
[подкоманде: Set-Image.](subcommand-set-image.md)
