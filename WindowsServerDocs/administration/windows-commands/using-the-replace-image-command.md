---
title: Replace-Image
description: Справочный раздел по Replace-Image, который заменяет существующий образ новой версией этого образа.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 68ded3df-e309-420f-9f5d-caeb609385a5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9dad35e54f064e02b863059ae6da9378403ee4f9
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720322"
---
# <a name="using-the-replace-image-command"></a>Использование команды replace-Image

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
носител<Image name>|Указывает имя заменяемого образа.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: {Загрузка &#124; установка}|Указывает тип заменяемого образа.|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Указывает архитектуру заменяемого образа. Так как в разных архитектурах можно использовать одинаковое имя образа для разных образов загрузки, указание архитектуры гарантирует замену нужного образа.|
|[/Филенаме:<File name>]|Если образ не может быть однозначно идентифицирован по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|/реплацементимаже|Задает параметры для замещающего изображения. Эти параметры задаются с помощью следующих параметров.<p>-mediaFile: <file path> — указывает имя и расположение (полный путь) для нового файла WIM.<br />-[/Саурцеимаже: <image name>] — указывает образ, используемый, если WIM-файл содержит несколько образов. Этот параметр применяется только к образам установки.<br />-[/Name:<Image name>] задает отображаемое имя образа.<br />-[/Description:<Image description>] — задает описание образа.|
## <a name="examples"></a>Примеры
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
## <a name="additional-references"></a>Дополнительные ссылки
- [Синтаксис](command-line-syntax-key.md)
командной строки[с помощью команды Add-](using-the-add-image-command.md)
Image с помощью команды "[Копировать](using-the-copy-image-command.md)
изображение" с помощью команды "[Export](using-the-export-image-command.md)

-Image" с[помощью команды "](using-the-get-image-command.md)[Replace](using-the-replace-image-command.md)
/Image" с командой "заменить на изображение[": Set-Image](subcommand-set-image.md)
