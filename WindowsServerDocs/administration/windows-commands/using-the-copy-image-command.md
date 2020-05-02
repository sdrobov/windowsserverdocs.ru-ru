---
title: Copy-Image
description: Справочный раздел по Copy-Image, который копирует образы, которые находятся в одной и той же группе образов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bea41cf4-36e6-4181-afa5-00170ebd4fdc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b3ffd590682ec36f78d3cbd53fd67fe3b5981e4c
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721000"
---
# <a name="copy-image"></a>Copy-Image

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует образы, которые находятся в одной и той же группе образов. Для копирования образов между группами образов используйте команду [Export-Image](using-the-export-image-command.md) , а затем команду [Add-Image](using-the-add-image-command.md) .

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
носител<Image name>|Задает имя копируемого образа.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: Установка|Указывает тип копируемого изображения. Этот параметр должен быть установлен в значение " **установить**".|
|\Медиаграуп:<Image group name>]|Указывает группу образов, содержащую копируемый образ. Если группа образов не указана и на сервере существует только одна группа, то эта группа образов будет использоваться по умолчанию. Если на сервере существует более одной группы образов, необходимо указать группу образов.|
|[/Филенаме:<Filename>]|Указывает имя файла копируемого образа. Если исходный образ не может быть однозначно определен по имени, необходимо указать имя файла.|
|/дестинатионимаже|Задает параметры для конечного образа, как описано в следующей таблице.<p>-/Name:<Name> -задает отображаемое имя копируемого образа.<br />-/Филенаме:<Filename> — задает имя конечного файла образа, который будет содержать копию образа.<br />-[/Description: <Description>] — Задает описание копии образа.|
## <a name="examples"></a>Примеры
Чтобы создать копию указанного образа и назовите ее Виндовсвиста. wim, введите:
```
wdsutil /copy-Imagmedia:Windows Vista with Officemediatype:Install /DestinationImage /Name:copy of Windows Vista with Office /Filename:WindowsVista.wim
```
Чтобы создать копию указанного образа, примените указанные параметры и назовите копию Виндовсвиста. wim, введите:
```
wdsutil /verbose /Progress /copy-Imagmedia:Windows Vista with Office /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:install.wim /DestinationImage /Name:copy of Windows Vista with Office /Filename:WindowsVista.wim /Description:This is a copy of the original Windows image with Office installed
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Синтаксис](command-line-syntax-key.md)
командной строки[с помощью команды Add-](using-the-add-image-command.md)
Image с помощью команды "[Export](using-the-export-image-command.md)
-Image" с помощью команды "[Открыть](using-the-get-image-command.md)
образ" с помощью инструкции[Remove](using-the-remove-image-command.md)
-Image с помощью команды[Replace](using-the-replace-image-command.md)
-Image[: Set-Image](subcommand-set-image.md)
