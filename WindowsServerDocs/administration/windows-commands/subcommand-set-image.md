---
title: Набор подкоманд-Image
description: Раздел команд Windows для подкоманд set-Image, который изменяет атрибуты изображения.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ae03c86-7a13-4e38-9182-32e55fffd504
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9564c489c1c3abced839ba27cbfe2841cd5894b0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833937"
---
# <a name="subcommand-set-image"></a>Подкоманда: Set-Image

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет атрибуты изображения.

## <a name="syntax"></a>Синтаксис
для загрузочных образов:
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
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носитель:<Image name>|Указывает имя образа.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: {Установка &#124; загрузки}|Указывает тип изображения.|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Указывает архитектуру образа. Поскольку одно и то же имя образа можно использовать для разных образов загрузки в разных архитектурах, указание архитектуры гарантирует, что образ будет изменен.|
|[/Филенаме:<File name>]|Если образ не может быть однозначно идентифицирован по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|/Name|Указывает имя образа.|
|/Description<Description>]|Задает описание образа.|
|[/Enabled: {Да &#124; }]|Включает или отключает образ.|
|\Медиаграуп:<Image group name>]|Указывает группу образов, содержащую образ. Если имя группы образов не указано и на сервере существует только одна группа образов, будет использоваться эта группа образов. Если на сервере существует несколько групп образов, необходимо использовать этот параметр, чтобы указать группу образов.|
|[/Усерфилтер:<SDDL>]|Задает фильтр пользователя на изображении. Строка фильтра должна быть в формате языка определения дескрипторов безопасности (SDDL). Обратите внимание, что, в отличие от параметра **/секурити** для групп образов, этот параметр запрещает только те, кто может видеть определение образа, а не фактические ресурсы файла изображения. Чтобы ограничить доступ к файловым ресурсам и, следовательно, доступ ко всем образам в группе образов, необходимо настроить безопасность для самой группы образов.|
|[/Unattendfile.:<Unattend file path>]|Задает полный путь к файлу автоматической установки, который должен быть связан с изображением. Например: **D:\Files\Unattend\Img1Unattend.XML**|
|[/Овервритеунаттенд: {Да &#124; }]|Можно указать параметр **/overwrite** , чтобы перезаписать файл автоматической установки, если файл автоматической установки, связанный с этим образом, уже существует. Обратите внимание, что значение по умолчанию — **нет**.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы задать значения для загрузочного образа, введите одно из следующих значений:
```
wdsutil /Set-Imagmedia:WinPE boot imagemediatype:Boot /Architecture:x86 /Description:New description
wdsutil /verbose /Set-Imagmedia:WinPE boot image /Server:MyWDSServemediatype:Boot /Architecture:x86 /Filename:boot.wim 
/Name:New Name /Description:New Description /Enabled:Yes
```
Чтобы задать значения для образа установки, введите одно из следующих значений:
```
wdsutil /Set-Imagmedia:Windows Vista with Officemediatype:Install /Description:New description 
wdsutil /verbose /Set-Imagmedia:Windows Vista with Office /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:install.wim /Name:New name /Description:New description /UserFilter:O:BAG:DUD:AI(A;ID;FA;;;SY)(A;ID;FA;;;BA)(A;ID;0x1200a9;;;AU) /Enabled:Yes /UnattendFile:\\server\share\unattend.xml /OverwriteUnattend:Yes
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[Использование команды add-Image](using-the-add-image-command.md)
[помощью команды Copy-](using-the-copy-image-command.md) Image
[с](using-the-export-image-command.md) помощью команды Get-Image
[помощью](using-the-get-image-command.md) команды [Remove](using-the-remove-image-command.md) -Image,
с помощью команды [Replace](using-the-replace-image-command.md) -Image.

