---
title: С помощью команды add образа
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5b6f4da-90ba-4b0e-9423-66c8ef5172e2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0433e0775bd2088170ae17fcfe432cdaee0bf99d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817465"
---
# <a name="using-the-add-image-command"></a>С помощью команды add образа

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

добавления образов на сервере служб развертывания Windows. Примеры об использовании этой команды, см. в разделе [примеры](#BKMK_examples).
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
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
mediaFile:<.wim file path>|Указывает полный путь и имя файла образа Windows (WIM), содержащей изображения должен быть добавлен.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
Тип носителя: {загрузки&#124;установить}|Задает тип изображения для добавления.|
|[/Skipverify]|Указывает, что проверка целостности, не быть выполнено на исходный файл изображения, прежде чем изображение будет добавлено.|
|[/ Name:<Name>]|Задает отображаемое имя изображения.|
|[/ Description:<Description>]|Задает описание образа.|
|[/ Filename:<Filename>]|Указывает имя нового файла WIM-файла. Это позволяет изменить имя файла WIM-файла, при добавлении изображения. Если имя файла не указано, будет использоваться имя исходного файла изображения. Во всех случаях служб развертывания Windows проверяет, чтобы определить, является ли имя файла уникальным в хранилище образов загрузки конечного компьютера.|
|\mediaGroup:<Image group name>]|Указывает имя группы образов, в которой будут добавляться изображения. Если на сервере существует более одной группы образов, необходимо указать группу образов. Если группы образов еще не существует, этот параметр не указан, будет создана новая группа образа. В противном случае будет использоваться существующие группы образов.|
|[/ SingleImage:<Single image name>] [/ Name:<Name>] [/ Description:<Description>]|Копирует указанное изображение одной из WIM-файл и задает изображение отображаемое имя и описание.|
|[/ UnattendFile:<Unattend file path>]|Указывает полный путь к файлу автоматической установки должны быть сопоставлены образы, которые добавляются. Если **/SingleImage** не указан, один и тот же файл автоматической установки, которые будут связаны с всех образов в WIM-файле.|
## <a name="BKMK_examples"></a>Примеры
Чтобы добавить загрузочный образ, введите следующую команду:
```
wdsutil /add-ImagmediaFile:"C:\MyFolder\Boot.wimmediatype:Boot
wdsutil /verbose /Progress /add-ImagmediaFile:\\MyServer\Share\Boot.wim /Server:MyWDSServemediatype:Boot /Name:"My WinPE Image" 
/Description:"WinPE Image containing the WDS Client" /Filename:WDSBoot.wim
```
Чтобы добавить образ установки, введите одно из следующих:
```
wdsutil /add-ImagmediaFile:"C:\MyFolder\Install.wimmediatype:Install
wdsutil /verbose /Progress /add-ImagmediaFile:\\MyServer\Share \Install.wim /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/SingleImage:"Windows Pro" /Name:"My WDS Image"
/Description:"Windows Pro image with Microsoft Office" /Filename:"Win Pro.wim" /UnattendFile:"\\server\share\unattend.xml"
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды копирования образа](using-the-copy-image-command.md)
[с помощью команды Export-Image](using-the-export-image-command.md)
[Using Команда Get-Image](using-the-get-image-command.md)
[с помощью команды remove образа](using-the-remove-image-command.md)
[с помощью команды заменить изображение](using-the-replace-image-command.md) 
 [ Подкоманда: set-Image](subcommand-set-image.md)
