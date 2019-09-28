---
title: Использование команды replace-Image
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68ded3df-e309-420f-9f5d-caeb609385a5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 52ad932cbdaca2c708add1a52677b5d7e84d9ed6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362734"
---
# <a name="using-the-replace-image-command"></a>Использование команды replace-Image

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

заменяет существующий образ новой версией этого образа.
## <a name="syntax"></a>Синтаксис
для загрузочных образов:
```
wdsutil [Options] /replace-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:Boot
     /Architecture:{x86 | ia64 | x64}
     [/Filename:<File name>]
     /replacementImage
       mediaFile:<wim file path>
         [/Name:<Image name>]
         [/Description:<Image description>]
```
для образов установки:
```
wdsutil [Options] /replace-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:Install
    mediaGroup:<Image group name>]
     [/Filename:<File name>]
     /replacementImage
       mediaFile:<wim file path>
         [/SourceImage:<Source image name>]
         [/Name:<Image name>]
         [/Description:<Image description>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носитель: <Image name>|Указывает имя заменяемого образа.|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: {Установка &#124; загрузки}|Указывает тип заменяемого образа.|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Указывает архитектуру заменяемого образа. Так как в разных архитектурах можно использовать одинаковое имя образа для разных образов загрузки, указание архитектуры гарантирует замену нужного образа.|
|[/Филенаме: <File name>]|Если образ не может быть однозначно идентифицирован по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|/реплацементимаже|Задает параметры для замещающего изображения. Эти параметры задаются с помощью следующих параметров.<br /><br />-mediaFile: <file path> — указывает имя и расположение (полный путь) нового WIM-файла.<br />-[/Саурцеимаже: <image name>] — указывает образ, используемый, если WIM-файл содержит несколько образов. Этот параметр применяется только к образам установки.<br />-[/Name: <Image name>] задает отображаемое имя образа.<br />-[/Description: <Image description>] — задает описание образа.|
## <a name="BKMK_examples"></a>Примеров
Чтобы заменить загрузочный образ, введите одно из следующих действий:
```
wdsutil /replace-Imagmedia:"WinPE Boot Imagemediatype:Boot /Architecture:x86 /replacementImagmediaFile:"C:\MyFolder\Boot.wim"
wdsutil /verbose /Progress /replace-Imagmedia:"WinPE Boot Image" /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filename:boot.wim 
/replacementImagmediaFile:\\MyServer\Share\Boot.wim /Name:"My WinPE Image" /Description:"WinPE Image with drivers"
```
Чтобы заменить образ установки, введите одно из следующих действий:
```
wdsutil /replace-Imagmedia:"Windows Vista Homemediatype:Install /replacementImagmediaFile:"C:\MyFolder\Install.wim"
wdsutil /verbose /Progress /replace-Imagmedia:"Windows Vista Pro" /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:Install.wim /replacementImagmediaFile:\\MyServer\Share \Install.wim /SourceImage:"Windows Vista Ultimate" /Name:"Windows Vista Desktop" /Description:"Windows Vista Ultimate with standard business applications."
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксис командной строки](command-line-syntax-key.md)
[с помощью команды add-Image](using-the-add-image-command.md)
 с помощью команды[Copy-](using-the-copy-image-command.md)Image @no__t[-5 с](using-the-export-image-command.md)помощью команды Get-Image, 
 с помощью[команды получения](using-the-get-image-command.md)изображения @no__t[-9 с помощью Команда Replace-Image](using-the-replace-image-command.md)1[подкоманда: Set-Image](subcommand-set-image.md)
