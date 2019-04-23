---
title: С помощью команды копирования образа
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 52c9c0bb45e60e76077bf90534e93f2c6fc1df18
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59884045"
---
# <a name="using-the-copy-image-command"></a>С помощью команды копирования образа

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует образы, которые находятся в той же группе образа. Чтобы копировать изображения между групп образов, используйте [с помощью команды Export-Image](using-the-export-image-command.md) команду и затем [с помощью команды add образа](using-the-add-image-command.md) команды.
Примеры об использовании этой команды, см. в разделе [примеры](#BKMK_examples).
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
мультимедиа:<Image name>|Указывает имя образа для копирования.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
MediaType:install|Задает тип изображения для копирования. Этот параметр должен быть установлен в **установить**.|
|\mediaGroup:<Image group name>]|Указывает группу образов, содержащий изображение для копирования. Если группа образа не указана, существует только одна группа на сервере по умолчанию будет использоваться этой группы образов. Если на сервере существует более одной группы образов, необходимо указать группу образов.|
|[/ Filename:<Filename>]|Указывает имя файла изображения для копирования. Если исходное изображение не может быть однозначно идентифицируется по имени, необходимо указать имя файла.|
|/DestinationImage|Задает параметры для конечного изображения, как описано в следующей таблице.<br /><br />-/ Name:<Name> -задает отображаемое имя изображения для копирования.<br />-/Filename:<Filename> — задает имя файла изображения назначения, который будет содержать копии образа.<br />-[/ Description: <Description>] — Задает описание копирования образа.|
## <a name="BKMK_examples"></a>Примеры
Чтобы создать копию указанное изображение и назовите его WindowsVista.wim, введите следующую команду:
```
wdsutil /copy-Imagmedia:"Windows Vista with Officemediatype:Install /DestinationImage /Name:"copy of Windows Vista with Office" /Filename:"WindowsVista.wim"
```
Чтобы создать копию заданного изображения, применить указанные параметры и назовите ее WindowsVista.wim, тип:
```
wdsutil /verbose /Progress /copy-Imagmedia:"Windows Vista with Office" /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:install.wim /DestinationImage /Name:"copy of Windows Vista with Office" /Filename:"WindowsVista.wim" /Description:"This is a copy of the original Windows image with Office installed"
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add образа](using-the-add-image-command.md)
[с помощью команды Export-Image](using-the-export-image-command.md)
[Using Команда Get-Image](using-the-get-image-command.md)
[с помощью команды remove образа](using-the-remove-image-command.md)
[с помощью команды заменить изображение](using-the-replace-image-command.md) 
 [ Подкоманда: set-Image](subcommand-set-image.md)
