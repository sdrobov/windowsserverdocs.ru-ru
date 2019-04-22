---
title: С помощью команды Export-Image
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a9b8b467-0f2d-4754-8998-55503a262778
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: efa9b2d09c37a383a91883ee02c995eedb2f235e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59823145"
---
# <a name="using-the-export-image-command"></a>С помощью команды Export-Image

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Экспортирует существующий образ из хранилища образов в другой файл образа Windows (WIM).
## <a name="syntax"></a>Синтаксис
для образов загрузки:
```
wdsutil [Options] /Export-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>]
     /DestinationImage
         /Filepath:<File path and name>
         [/Name:<Name>]
         [/Description:<Description>]
     [/Overwrite:{Yes | No}]
```
для образов установки:
```
wdsutil [Options] /Export-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:InstallmediaGroup:<Image group name>]
     [/Filename:<File name>]
     /DestinationImage
         /Filepath:<File path and name>
         [/Name:<Name>]
         [/Description:<Description>]
     [/Overwrite:{Yes | No | append}]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
мультимедиа:<Image name>|Задает имя изображения для экспорта.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
Тип носителя: {загрузки &#124; установить}|Задает тип изображения для экспорта.|
|\mediaGroup:<Image group name>]|Указывает группу образов, содержащий изображение для экспорта. Если указано имя группы не образа и только один образ группа существует на сервере, по умолчанию будет использоваться этой группы образов. Если на сервере существует более одной группы образов, необходимо указать группу образов.|
|/ Архитектура: {x86 &#124; ia64 &#124; x64}|Задает архитектуру изображения для экспорта. Так как это может быть то же имя образа для загрузочных образов в различных архитектур, значение архитектуры гарантирует, что правильное изображение будет возвращаться.|
|[/ Filename:<Filename>]|Если изображение не может быть однозначно идентифицируется по имени, необходимо указать имя файла.|
|/DestinationImage|Задает параметры для конечного изображения. Можно указать эти параметры, используя следующие параметры:<br /><br />-/Filepath:<File path and name> -указывает полный путь для нового образа.<br />-[/ Name:<Name>] — Задает отображаемое имя изображения. Если имя не указано, будет использоваться отображаемое имя исходного изображения.<br />-[/ Description: <Description>] — Задает описание образа.|
|[/ Overwrite: {Да &#124; нет &#124; append}]|Определяет, является ли файл, указанный в **/DestinationImage** параметр будут перезаписаны, если существующий файл с таким именем уже существует в /Filepath.<br /><br />-   **Да** вызывает перезапись существующего файла.<br />-   **Не** (параметр по умолчанию), приводит к ошибке в случае, если файл с таким именем уже существует.<br />-   **Добавление** вызывает созданное изображение для добавления в качестве образа в существующий WIM-файл.|
## <a name="BKMK_examples"></a>Примеры
Чтобы экспортировать образ загрузки, введите одно из следующих:
```
wdsutil /Export-Imagmedia:"WinPE boot imagemediatype:Boot /Architecture:x86 /DestinationImage /Filepath:"C:\temp\boot.wim"
wdsutil /verbose /Progress /Export-Imagmedia:"WinPE boot image" /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filename:boot.wim 
/DestinationImage /Filepath:"\\Server\Share\ExportImage.wim" /Name:"Exported WinPE image" /Description:"WinPE Image from WDS server" /Overwrite:Yes
```
Чтобы экспортировать образ установки, введите одно из следующих:
```
wdsutil /Export-Imagmedia:"Windows Vista with Officemediatype:Install /DestinationImage /Filepath:"C:\Temp\Install.wim"
wdsutil /verbose /Progress /Export-Imagmedia:"Windows Vista with Office" /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:install.wim /DestinationImage /Filepath:\\server\share\export.wim /Name:"Exported Windows image" /Description:"Windows Vista image from WDS server" /Overwrite:append
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add образа](using-the-add-image-command.md)
[с помощью команды копирования образа](using-the-copy-image-command.md)
[с помощью get образа Команда](using-the-get-image-command.md)
[с помощью команды remove образа](using-the-remove-image-command.md)
[с помощью команды заменить изображение](using-the-replace-image-command.md)
[подкоманда : set-Image](subcommand-set-image.md)
