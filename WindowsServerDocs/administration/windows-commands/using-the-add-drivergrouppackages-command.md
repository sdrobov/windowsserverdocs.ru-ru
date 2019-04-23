---
title: С помощью команды add-DriverGroupPackages
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 29022f53-ce14-4b2d-a81a-679c18e022b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ad0f8c7ed202f0d6fccc11307b17b742c70c3e49
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842795"
---
# <a name="using-the-add-drivergrouppackages-command"></a>С помощью команды add-DriverGroupPackages

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Примеры об использовании этой команды, см. в разделе [примеры](#BKMK_examples).
## <a name="syntax"></a>Синтаксис
```
wdsutil /add-DriverGroupPackages /DriverGroup:<Group Name> [/Server:<Server Name>] /Filtertype:<Filter type> /Operator:{Equal | NotEqual | GreaterOrEqual | LessOrEqual | Contains} /Value:<Value> [/Value:<Value>
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ DriverGroup:<Group Name>|Задает имя группы драйверов.|
|/ Server:<Server name>|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.|
|/ Filtertype:<Filter type>|Указывает атрибут пакета драйвера для поиска. В рамках одной команды можно указать несколько атрибутов. Если этот параметр, необходимо также указать /Operator и /Value.<br /><br /><Filter type> Может принимать одно из следующих:<br /><br />**PackageId**<br /><br />**Имя пакета**<br /><br />**PackageEnabled**<br /><br />**Packagedateadded**<br /><br />**PackageInfFilename**<br /><br />**PackageClass**<br /><br />**PackageProvider**<br /><br />**PackageArchitecture**<br /><br />**PackageLocale**<br /><br />**PackageSigned**<br /><br />**PackagedatePublished**<br /><br />**Packageversion**<br /><br />**Driverdescription**<br /><br />**DriverManufacturer**<br /><br />**DriverHardwareId**<br /><br />**DrivercompatibleId**<br /><br />**DriverExcludeId**<br /><br />**DriverGroupId**<br /><br />**DriverGroupName**|
|/Operator:{Equal &#124; NotEqual &#124; GreaterOrEqual &#124; LessOrEqual &#124; Contains}|Задает связь между атрибутом и значения. Можно указать только **Contains** со строковыми атрибутами. Можно указать только **равно**, **NotEqual**, **GreaterOrEqual** и **LessOrEqual** с атрибутами даты и версии.|
|-Значение:<Value>|Указывает клиента значение, соответствующее **/Filtertype**. Можно указать несколько значений для одного **/Filtertype**. В следующем списке приведены значения, которые можно указать для каждого фильтра. Дополнительные сведения об этих значениях см. в разделе [атрибуты драйверов и пакетов](https://go.microsoft.com/fwlink/?LinkId=166895) (https://go.microsoft.com/fwlink/?LinkId=166895).<br /><br />-PackageId - укажите допустимый GUID. Например: {4d36e972-e325-11ce-bfc1-08002be10318}.<br />— Укажите имя пакета любое строковое значение.<br />-Укажите PackageEnabled - **Да** или **нет**.<br />-Packagedateadded - укажите дату в следующем формате: ГГГГ/ММ/ДД<br />-Укажите PackageInfFilename любое строковое значение.<br />-PackageClass - укажите допустимое имя класса или идентификатор GUID класса. Пример: **Поставляется**, **Net**, или {4d36e972-e325-11ce-bfc1-08002be10318}.<br />-Укажите PackageProvider любое строковое значение.<br />-Укажите PackageArchitecture - **x86**, **x64**, или **ia64**.<br />-PackageLoale - указать, является допустимым идентификатором языка. Например: **en US** или **es-ES**.<br />-Укажите PackageSigned - **Да** или **нет**.<br />-PackagedatePublished - укажите дату в следующем формате: ГГГГ/ММ/ДД<br />-Packageversion - версия указывается в следующем формате: a.b.x.y. Пример: 6.1.0.0<br />-Укажите Driverdescription любое строковое значение.<br />-Укажите DriverManufacturer любое строковое значение.<br />-DriverHardwareId - укажите любое строковое значение.<br />-DrivercompatibleId - укажите любое строковое значение.<br />-DriverExcludeId - укажите любое строковое значение.<br />-DriverGroupId - укажите допустимый GUID. Например: {4d36e972-e325-11ce-bfc1-08002be10318}.<br />-Укажите DriverGroupName любое строковое значение.|
## <a name="BKMK_examples"></a>Примеры
Чтобы добавить пакет драйвера, введите одно из следующих:
```
wdsutil /verbose /add-DriverGroupPackages /DriverGroup:printerdrivers /Filtertype:PackageClass /Operator:Equal /Value:printer /Filtertype:DriverManufacturer /Operator:NotEqual /Value:Name1 /Value:Name2
```
```
wdsutil /verbose /add-DriverGroupPackages /DriverGroup:DisplayDriversX86 /Filtertype:PackageClass /Operator:Equal /Value:Display /Filtertype:PackageArchitecture /Operator:Equal /Value:x86 /Filtertype:Packagedateadded /Operator:LessOrEqual /Value:2008/01/01
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add-DriverGroupPackage](using-the-add-drivergrouppackage-command.md)
[с помощью команды add-DriverPackage](using-the-add-driverpackage-command.md) 
 [Помощью add-AllDriverPackages подкоманды](using-the-add-alldriverpackages-subcommand.md)
