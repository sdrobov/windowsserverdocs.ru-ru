---
title: С помощью команды add-ImageDriverPackages
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9dc78909-a4d1-42a2-af8f-21ebcbfe8302
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 55b26acf9c4006db3d64e27be8a10e158876ddc1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817365"
---
# <a name="using-the-add-imagedriverpackages-command"></a>С помощью команды add-ImageDriverPackages

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет пакеты драйверов из хранилища драйверов в загрузочный образ. Версия образа должна быть Windows 7 или Windows Server 2008 R2 или более поздней версии.
Примеры об использовании этой команды, см. в разделе [примеры](#BKMK_examples).
## <a name="syntax"></a>Синтаксис
```
wdsutil /add-ImageDriverPackages [/Server:<Server name>media:<Image namemediatype:Boot /Architecture:{x86 | ia64 | x64} 
[/Filename:<File name>] /Filtertype:<Filter type> /Operator:{Equal | NotEqual | GreaterOrEqual | LessOrEqual | Contains} /Value:<Value> [/Value:<Value> ...]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ Server:<Server name>|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.|
мультимедиа:<Image name>|Указывает имя образа, чтобы добавить драйвер.|
MediaType:Boot|Задает тип изображения, чтобы добавить драйвер. Пакеты драйверов могут добавляться только в образы загрузки.|
|/ Архитектура: {x86 &#124; ia64 &#124; x64}|Задает архитектуру загрузочного образа. Так как это может быть то же имя образа для загрузочных образов в различных архитектур, следует указать архитектуры, чтобы убедиться, что используется правильный образ.|
|/ Имя файла:<File name>|Указывает имя файла. Если изображение не может быть однозначно идентифицируется по имени, необходимо указать имя файла.|
|/ Filtertype:<Filter type>|Указывает атрибут пакета драйвера для поиска. В рамках одной команды можно указать несколько атрибутов. Необходимо также указать **/Operator** и **/Value** с этим параметром.<br /><br /><Filter type> Может принимать одно из следующих:<br /><br />**PackageId**<br /><br />**Имя пакета**<br /><br />**PackageEnabled**<br /><br />**Packagedateadded**<br /><br />**PackageInfFilename**<br /><br />**PackageClass**<br /><br />**PackageProvider**<br /><br />**PackageArchitecture**<br /><br />**PackageLocale**<br /><br />**PackageSigned**<br /><br />**PackagedatePublished**<br /><br />**Packageversion**<br /><br />**Driverdescription**<br /><br />**DriverManufacturer**<br /><br />**DriverHardwareId**<br /><br />**DrivercompatibleId**<br /><br />**DriverExcludeId**<br /><br />**DriverGroupId**<br /><br />**DriverGroupName**|
|/Operator:{Equal &#124; NotEqual &#124; GreaterOrEqual &#124; LessOrEqual &#124; Contains}|Связь между атрибутом и значения. Можно указать только **Contains** со строковыми атрибутами. Можно указать только **GreaterOrEqual** и **LessOrEqual** с атрибутами даты и версии.|
|-Значение:<Value>|Указывает значение для поиска относительно указанного <attribute>. Можно указать несколько значений для одного **/Filtertype**. В списке ниже представлены атрибуты, которые можно указать для каждого фильтра. Дополнительные сведения об этих атрибутах см. в разделе [атрибуты драйверов и пакетов](https://go.microsoft.com/fwlink/?LinkId=166895) (https://go.microsoft.com/fwlink/?LinkId=166895).<br /><br />-PackageId - укажите допустимый GUID. Например: {4d36e972-e325-11ce-bfc1-08002be10318}.<br />— Укажите имя пакета любое строковое значение.<br />-Укажите PackageEnabled - **Да** или **нет**.<br />-Packagedateadded - укажите дату в следующем формате: ГГГГ/ММ/ДД<br />-Укажите PackageInfFilename любое строковое значение.<br />-PackageClass - укажите допустимое имя класса или идентификатор GUID класса. Пример: **Поставляется**, **Net**, или {4d36e972-e325-11ce-bfc1-08002be10318}.<br />-Укажите PackageProvider любое строковое значение.<br />-Укажите PackageArchitecture - **x86**, **x64**, или **ia64**.<b /> -PackageLocale - указать, является допустимым идентификатором языка. Например: **en US** или **es-ES**.<br />-Укажите PackageSigned - **Да** или **нет**.<br />-PackagedatePublished - укажите дату в следующем формате: ГГГГ/ММ/ДД<br />-Packageversion - версия указывается в следующем формате: a.b.x.y. Пример: 6.1.0.0<br />-Укажите Driverdescription любое строковое значение.<br />-Укажите DriverManufacturer любое строковое значение.<br />-DriverHardwareId - укажите любое строковое значение.<br />-DrivercompatibleId - укажите любое строковое значение.<br />-DriverExcludeId - укажите любое строковое значение.<br />-DriverGroupId - укажите допустимый GUID. Например: {4d36e972-e325-11ce-bfc1-08002be10318}.<br />-Укажите DriverGroupName любое строковое значение.|
## <a name="BKMK_examples"></a>Примеры
Чтобы добавить пакеты драйверов в загрузочный образ, введите одно из следующих:
```
wdsutil /add-ImageDriverPackagemedia:"WinPE Boot Imagemediatype:Boot /Architecture:x86 /Filtertype:DriverGroupName /Operator:Equal /Value:x86Bus /Filtertype:PackageProvider /Operator:Contains /Value:Provider1 /Filtertype:Packageversion /Operator:GreaterOrEqual /Value:6.1.0.0
```
```
wdsutil /verbose /add-ImageDriverPackagemedia: "WinPE Boot Image" /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filtertype:PackageClass /Operator:Equal /Value:Net /Filtertype:DriverManufacturer /Operator:NotEqual /Value:Name1 /Value:Name2 /Filtertype:Packagedateadded /Operator:LessOrEqual /Value:2008/01/01
```
```
wdsutil /verbose /add-ImageDriverPackagemedia:"WinPE Boot Image" /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filtertype:PackageClass /Operator:Equal /Value:Net /Value:System /Value:DiskDrive /Value:HDC /Value:SCSIAdapter
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add-ImageDriverPackage](using-the-add-imagedriverpackage-command.md)
[помощью add-AllDriverPackages подкоманды](using-the-add-alldriverpackages-subcommand.md)
