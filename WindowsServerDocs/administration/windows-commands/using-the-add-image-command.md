---
title: добавить-изображение
description: Раздел команд Windows для Add-Image, который добавляет образы на сервер служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d5b6f4da-90ba-4b0e-9423-66c8ef5172e2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6888027e3f5f7f44f2b37e958d0f779431e994a9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831977"
---
# <a name="add-image"></a>добавить-изображение

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет образы на сервер служб развертывания Windows. Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).

## <a name="syntax"></a>Синтаксис
для загрузочных образов используйте следующий синтаксис:
```
wdsutil /add-ImagmediaFile:<wim file path> [/Server:<Server name>mediatype:Boot [/Skipverify] [/Name:<Image name>] [/Description:<Image description>] 
[/Filename:<New wim file name>]
```
для образов установки используйте следующий синтаксис:
```
wdsutil /add-ImagmediaFile:<wim file path>
     [/Server:<Server name>]
   mediatype:Install
     [/Skipverify]
    mediaGroup:<Image group name>]
     [/SingleImage:<Single image name>]
         [/Name:<Name>]
         [/Description:<Description>]
     [/Filename:<File name>]
     [/UnattendFile:<Unattend file path>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
mediaFile: путь к файлу <. wim >|Указывает полный путь и имя файла образа Windows (WIM-файла), содержащего добавляемые образы.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: {Установка&#124;загрузки}|Указывает тип добавляемых образов.|
|[/Скипверифи]|Указывает, что проверка целостности не будет выполняться для исходного файла изображения перед добавлением образа.|
|[/Name:<Name>]|Задает отображаемое имя изображения.|
|/Description<Description>]|Задает описание образа.|
|[/Филенаме:<Filename>]|Указывает новое имя файла для WIM-файла. Это позволяет изменить имя файла WIM при добавлении образа. Если имя файла не указано, будет использоваться имя файла исходного изображения. Во всех случаях службы развертывания Windows проверяют, является ли имя файла уникальным в хранилище загрузочных образов конечного компьютера.|
|\Медиаграуп:<Image group name>]|Указывает имя группы образов, в которую будут добавлены образы. Если на сервере существует более одной группы образов, необходимо указать группу образов. Если этот элемент не указан и группа образов еще не существует, будет создана новая группа образов. В противном случае будет использоваться существующая группа образов.|
|[/Синглеимаже:<Single image name>] [/Name:<Name>] /Description<Description>]|Копирует указанный отдельный образ из WIM-файла и задает отображаемое имя и описание образа.|
|[/Unattendfile.:<Unattend file path>]|Указывает полный путь к файлу автоматической установки, который будет связан с добавляемыми изображениями. Если **/синглеимаже** не указан, то тот же файл автоматической установки будет связан со всеми образами в WIM-файле.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы добавить загрузочный образ, введите:
```
wdsutil /add-ImagmediaFile:C:\MyFolder\Boot.wimmediatype:Boot
wdsutil /verbose /Progress /add-ImagmediaFile:\\MyServer\Share\Boot.wim /Server:MyWDSServemediatype:Boot /Name:My WinPE Image 
/Description:WinPE Image containing the WDS Client /Filename:WDSBoot.wim
```
Чтобы добавить образ установки, введите одно из следующих действий:
```
wdsutil /add-ImagmediaFile:C:\MyFolder\Install.wimmediatype:Install
wdsutil /verbose /Progress /add-ImagmediaFile:\\MyServer\Share \Install.wim /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/SingleImage:Windows Pro /Name:My WDS Image
/Description:Windows Pro image with Microsoft Office /Filename:Win Pro.wim /UnattendFile:\\server\share\unattend.xml
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[Использование команды copy-](using-the-copy-image-command.md) Image
[помощью команды Export-](using-the-export-image-command.md) Image
помощью команды [Get-](using-the-get-image-command.md) Image
[помощью команды Remove](using-the-remove-image-command.md) -image,
[с помощью команды replace-](using-the-replace-image-command.md) Image
[подкоманде: Set-Image.](subcommand-set-image.md)
