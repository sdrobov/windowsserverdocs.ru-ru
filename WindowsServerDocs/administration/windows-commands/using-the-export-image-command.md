---
title: Export-Image
description: Справочный раздел по Export-Image, который экспортирует существующий образ из хранилища образов в другой файл образа Windows (WIM).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a9b8b467-0f2d-4754-8998-55503a262778
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 477859687732fa2cccdc782edb81fdd348f313c5
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720915"
---
# <a name="export-image"></a>Export-Image

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Экспортирует существующий образ из хранилища образов в другой файл образа Windows (WIM).

## <a name="syntax"></a>Синтаксис
для загрузочных образов:
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
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носител<Image name>|Указывает имя экспортируемого образа.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: {Загрузка &#124; установка}|Указывает тип экспортируемого изображения.|
|\Медиаграуп:<Image group name>]|Указывает группу образов, содержащую экспортируемый образ. Если имя группы образов не указано и на сервере существует только одна группа образов, то эта группа образов будет использоваться по умолчанию. Если на сервере существует более одной группы образов, необходимо указать группу образов.|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Определяет архитектуру экспортируемого образа. Так как для образов загрузки в разных архитектурах можно использовать одно и то же имя образа, задание значения архитектуры гарантирует, что будет возвращен правильный образ.|
|[/Филенаме:<Filename>]|Если образ не может быть однозначно определен по имени, необходимо указать имя файла.|
|/дестинатионимаже|Задает параметры для конечного образа. Эти параметры можно указать с помощью следующих параметров.<p>-/FilePath.:<File path and name> — указывает полный путь к файлу для нового образа.<br />-[/Name:<Name>] — задает отображаемое имя образа. Если имя не указано, будет использоваться отображаемое имя исходного изображения.<br />-[/Description: <Description>] — Задает описание образа.|
|[/Overwrite: {Да &#124; нет &#124; Append}]|Определяет, будет ли перезаписан файл, указанный в параметре **/дестинатионимаже** , если существующий файл с таким именем уже существует в/филепас.<p>-   **Да** , приводит к перезаписанию существующего файла.<br />-   **Нет** (параметр по умолчанию) приводит к возникновению ошибки, если файл с таким именем уже существует.<br />-   **append** приводит к добавлению созданного образа в качестве нового образа в существующий WIM-файл.|
## <a name="examples"></a>Примеры
Чтобы экспортировать загрузочный образ, введите один из следующих элементов:
```
wdsutil /Export-Imagmedia:WinPE boot imagemediatype:Boot /Architecture:x86 /DestinationImage /Filepath:C:\temp\boot.wim
wdsutil /verbose /Progress /Export-Imagmedia:WinPE boot image /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filename:boot.wim 
/DestinationImage /Filepath:\\Server\Share\ExportImage.wim /Name:Exported WinPE image /Description:WinPE Image from WDS server /Overwrite:Yes
```
Чтобы экспортировать образ установки, введите одно из следующих действий:
```
wdsutil /Export-Imagmedia:Windows Vista with Officemediatype:Install /DestinationImage /Filepath:C:\Temp\Install.wim
wdsutil /verbose /Progress /Export-Imagmedia:Windows Vista with Office /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:install.wim /DestinationImage /Filepath:\\server\share\export.wim /Name:Exported Windows image /Description:Windows Vista image from WDS server /Overwrite:append
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Синтаксис](command-line-syntax-key.md)
командной строки[с помощью команды Add-](using-the-add-image-command.md)
Image с помощью команды[Copy-](using-the-copy-image-command.md)
Image с командой[Get](using-the-get-image-command.md)
-Image с помощью команды[Remove](using-the-remove-image-command.md)
-Image с помощью команды[Replace](using-the-replace-image-command.md)
-Image[: Set-Image](subcommand-set-image.md)
