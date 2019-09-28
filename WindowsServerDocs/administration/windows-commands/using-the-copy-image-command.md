---
title: Использование команды Copy-Image
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bea41cf4-36e6-4181-afa5-00170ebd4fdc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2f269884e9c1f96151c9e1220242fad917b76831
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363565"
---
# <a name="using-the-copy-image-command"></a>Использование команды Copy-Image

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носитель: <Image name>|Задает имя копируемого образа.|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: Установка|Указывает тип копируемого изображения. Этот параметр должен быть установлен в значение " **установить**".|
|\Медиаграуп: <Image group name>]|Указывает группу образов, содержащую копируемый образ. Если группа образов не указана и на сервере существует только одна группа, то эта группа образов будет использоваться по умолчанию. Если на сервере существует более одной группы образов, необходимо указать группу образов.|
|[/Филенаме: <Filename>]|Указывает имя файла копируемого образа. Если исходный образ не может быть однозначно определен по имени, необходимо указать имя файла.|
|/дестинатионимаже|Задает параметры для конечного образа, как описано в следующей таблице.<br /><br />-/Name: <Name> — задает отображаемое имя копируемого образа.<br />-/Филенаме: <Filename> — задает имя конечного файла образа, который будет содержать копию образа.<br />-[/Description: <Description>] — Задает описание копии образа.|
## <a name="BKMK_examples"></a>Примеров
Чтобы создать копию указанного образа и назовите ее Виндовсвиста. wim, введите:
```
wdsutil /copy-Imagmedia:"Windows Vista with Officemediatype:Install /DestinationImage /Name:"copy of Windows Vista with Office" /Filename:"WindowsVista.wim"
```
Чтобы создать копию указанного образа, примените указанные параметры и назовите копию Виндовсвиста. wim, введите:
```
wdsutil /verbose /Progress /copy-Imagmedia:"Windows Vista with Office" /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:install.wim /DestinationImage /Name:"copy of Windows Vista with Office" /Filename:"WindowsVista.wim" /Description:"This is a copy of the original Windows image with Office installed"
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксис командной строки](command-line-syntax-key.md)
[с помощью команды add-Image](using-the-add-image-command.md)
 с[помощью команды Export-Image](using-the-export-image-command.md)
 с помощью команды[Get](using-the-get-image-command.md)-Image 
 с помощью[команды Remove-](using-the-remove-image-command.md)Image @no__t[-9 с помощью Команда Replace-Image](using-the-replace-image-command.md)1[подкоманда: Set-Image](subcommand-set-image.md)
