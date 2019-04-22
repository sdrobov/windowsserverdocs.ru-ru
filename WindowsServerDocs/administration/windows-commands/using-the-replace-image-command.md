---
title: С помощью команды заменить изображение
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: e396ee678e22885a50c02800d77ecea1cc5ef8ba
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59819655"
---
# <a name="using-the-replace-image-command"></a>С помощью команды заменить изображение

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

заменяет существующий образ до новой версии этого образа.
## <a name="syntax"></a>Синтаксис
для образов загрузки:
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
мультимедиа:<Image name>|Указывает имя образа, чтобы заменить.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
Тип носителя: {загрузки &#124; установить}|Задает тип изображения, чтобы заменить.|
|/ Архитектура: {x86 &#124; ia64 &#124; x64}|Задает архитектуру изображения заменяемого. Так как это может быть то же имя образа для различных загрузочных образов в различных архитектур, указав архитектуру гарантирует, что заменяется нужного образа.|
|[/ Filename:<File name>]|Если изображение не может быть однозначно идентифицируется по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|/replacementImage|Задает параметры для замены образа. Можно задать эти параметры, используя следующие параметры:<br /><br />-mediaFile: <file path> -указывает имя и расположение (полный путь) в новый WIM-файла.<br />-[/ Является: <image name>] — Задает изображение, используемое, если в WIM-файл содержит несколько образов. Этот параметр применяется только для установки образов.<br />-[/ Name:<Image name>] Задает отображаемое имя изображения.<br />-[/ Description:<Image description>] — Задает описание образа.|
## <a name="BKMK_examples"></a>Примеры
Чтобы заменить образ загрузки, введите одно из следующих:
```
wdsutil /replace-Imagmedia:"WinPE Boot Imagemediatype:Boot /Architecture:x86 /replacementImagmediaFile:"C:\MyFolder\Boot.wim"
wdsutil /verbose /Progress /replace-Imagmedia:"WinPE Boot Image" /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filename:boot.wim 
/replacementImagmediaFile:\\MyServer\Share\Boot.wim /Name:"My WinPE Image" /Description:"WinPE Image with drivers"
```
Чтобы заменить образ установки, введите одно из следующих:
```
wdsutil /replace-Imagmedia:"Windows Vista Homemediatype:Install /replacementImagmediaFile:"C:\MyFolder\Install.wim"
wdsutil /verbose /Progress /replace-Imagmedia:"Windows Vista Pro" /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:Install.wim /replacementImagmediaFile:\\MyServer\Share \Install.wim /SourceImage:"Windows Vista Ultimate" /Name:"Windows Vista Desktop" /Description:"Windows Vista Ultimate with standard business applications."
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add образа](using-the-add-image-command.md)
[с помощью команды копирования образа](using-the-copy-image-command.md)
[Using Команда export-Image](using-the-export-image-command.md)
[с помощью команды get образа](using-the-get-image-command.md)
[с помощью команды заменить изображение](using-the-replace-image-command.md) 
 [ Подкоманда: set-Image](subcommand-set-image.md)
