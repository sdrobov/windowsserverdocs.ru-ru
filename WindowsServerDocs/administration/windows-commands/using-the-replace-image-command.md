---
title: Replace-Image
description: Раздел команд Windows для Replace-Image, который заменяет существующий образ новой версией этого образа.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 68ded3df-e309-420f-9f5d-caeb609385a5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8d16ec07171e4560af8074cb9b0be7b6dc252119
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830227"
---
# <a name="using-the-replace-image-command"></a>Использование команды replace-Image

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Заменяет существующий образ новой версией этого образа.
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
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носитель:<Image name>|Указывает имя заменяемого образа.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: {Установка &#124; загрузки}|Указывает тип заменяемого образа.|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Указывает архитектуру заменяемого образа. Так как в разных архитектурах можно использовать одинаковое имя образа для разных образов загрузки, указание архитектуры гарантирует замену нужного образа.|
|[/Филенаме:<File name>]|Если образ не может быть однозначно идентифицирован по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|/реплацементимаже|Задает параметры для замещающего изображения. Эти параметры задаются с помощью следующих параметров.<p>-mediaFile: <file path> — указывает имя и расположение (полный путь) нового WIM-файла.<br />-[/Саурцеимаже: <image name>] — указывает образ, используемый, если WIM-файл содержит несколько образов. Этот параметр применяется только к образам установки.<br />-[/Name:<Image name>] задает отображаемое имя образа.<br />-[/Description:<Image description>] — задает описание образа.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы заменить загрузочный образ, введите одно из следующих действий:
```
wdsutil /replace-Imagmedia:WinPE Boot Imagemediatype:Boot /Architecture:x86 /replacementImagmediaFile:C:\MyFolder\Boot.wim
wdsutil /verbose /Progress /replace-Imagmedia:WinPE Boot Image /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filename:boot.wim 
/replacementImagmediaFile:\\MyServer\Share\Boot.wim /Name:My WinPE Image /Description:WinPE Image with drivers
```
Чтобы заменить образ установки, введите одно из следующих действий:
```
wdsutil /replace-Imagmedia:Windows Vista Homemediatype:Install /replacementImagmediaFile:C:\MyFolder\Install.wim
wdsutil /verbose /Progress /replace-Imagmedia:Windows Vista Pro /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:Install.wim /replacementImagmediaFile:\\MyServer\Share \Install.wim /SourceImage:Windows Vista Ultimate /Name:Windows Vista Desktop /Description:Windows Vista Ultimate with standard business applications.
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[Использование команды add-Image](using-the-add-image-command.md)
[помощью команды Copy-](using-the-copy-image-command.md) Image
помощью команды [Export-](using-the-export-image-command.md) image
[помощью команды Get](using-the-get-image-command.md) -image,
[с помощью команды replace-](using-the-replace-image-command.md) Image
[подкоманде: Set-Image.](subcommand-set-image.md)
