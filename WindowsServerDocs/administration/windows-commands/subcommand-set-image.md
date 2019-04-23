---
title: Подкоманды set-Image
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2ae03c86-7a13-4e38-9182-32e55fffd504
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e63c67210764de76edae18a1897a68d763f9d695
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59856485"
---
# <a name="subcommand-set-image"></a>Подкоманда: set-Image

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет атрибуты изображения.
## <a name="syntax"></a>Синтаксис
для образов загрузки:
```
wdsutil /Set-Imagmedia:<Image name> [/Server:<Server name>mediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>] [/Name:<Name>] 
[/Description:<Description>] [/Enabled:{Yes | No}]
```
для образов установки:
```
wdsutil /Set-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:InstallmediaGroup:<Image group name>]
     [/Filename:<File name>]
     [/Name:<Name>]
     [/Description:<Description>]
     [/UserFilter:<SDDL>]
     [/Enabled:{Yes | No}]
     [/UnattendFile:<Unattend file path>]
         [/OverwriteUnattend:{Yes | No}]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
мультимедиа:<Image name>|Задает имя образа.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
Тип носителя: {загрузки &#124; установить}|Задает тип изображения.|
|/ Архитектура: {x86 &#124; ia64 &#124; x64}|Задает архитектуру изображения. Так как в различных архитектур, может иметь одно и то же имя образа для различных загрузочных образов, указание архитектуры гарантирует, правильное изображение было изменено.|
|[/ Filename:<File name>]|Если изображение не может быть однозначно идентифицируется по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|[/ Name]|Задает имя образа.|
|[/ Description:<Description>]|Задает описание образа.|
|[/ Включен: {Да &#124; No}]|Включает или отключает изображение.|
|\mediaGroup:<Image group name>]|Указывает группу образов, содержащий изображение. Если указано имя группы не образа и только один образ группа существует на сервере, будет использоваться этой группы образов. Если на сервере существует более одной группы образов, необходимо использовать этот параметр, чтобы указать группу образов.|
|[/ UserFilter:<SDDL>]|Задает фильтр пользователя на изображении. Строка фильтра должен быть в формате языка определения дескрипторов безопасности (SDDL). Обратите внимание, что, в отличие от **/Security** параметр для групп образов, этот параметр ограничивает только кто может просматривать в определении образа и не фактическое изображение файловых ресурсов. Чтобы ограничить доступ к файловым ресурсам и таким образом доступ все образы в группу образов, необходимо будет настроить безопасность для самой группе, изображение.|
|[/ UnattendFile:<Unattend file path>]|Задает полный путь к файлу автоматической установки связываемых с изображением. Пример: **D:\Files\Unattend\Img1Unattend.xml**|
|[/ OverwriteUnattend: {Да &#124; No}]|Можно указать **/Overwrite** перезаписать файл автоматической установки, если уже существует файл автоматической установки, связанный с изображением. Обратите внимание, что значение по умолчанию — **нет**.|
## <a name="BKMK_examples"></a>Примеры
Чтобы задать значения для загрузочного образа, введите одно из следующих:
```
wdsutil /Set-Imagmedia:"WinPE boot imagemediatype:Boot /Architecture:x86 /Description:"New description"
wdsutil /verbose /Set-Imagmedia:"WinPE boot image" /Server:MyWDSServemediatype:Boot /Architecture:x86 /Filename:boot.wim 
/Name:"New Name" /Description:"New Description" /Enabled:Yes
```
Чтобы задать значения для образа установки, введите одно из следующих:
```
wdsutil /Set-Imagmedia:"Windows Vista with Officemediatype:Install /Description:"New description" 
wdsutil /verbose /Set-Imagmedia:"Windows Vista with Office" /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:install.wim /Name:"New name" /Description:"New description" /UserFilter:"O:BAG:DUD:AI(A;ID;FA;;;SY)(A;ID;FA;;;BA)(A;ID;0x1200a9;;;AU)" /Enabled:Yes /UnattendFile:\\server\share\unattend.xml /OverwriteUnattend:Yes
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add образа](using-the-add-image-command.md)
[с помощью команды копирования образа](using-the-copy-image-command.md)
[Using Команда export-Image](using-the-export-image-command.md)
[с помощью команды get образа](using-the-get-image-command.md)
[с помощью команды remove образа](using-the-remove-image-command.md) 
 [ С помощью команды заменить изображение](using-the-replace-image-command.md)
