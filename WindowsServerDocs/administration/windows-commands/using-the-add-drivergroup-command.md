---
title: С помощью команды add-DriverGroup
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a92fe8f-03f9-462a-b99e-f23275259807
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 322a9a671f90bf56f6357289f7727c142a0145cc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825095"
---
# <a name="using-the-add-drivergroup-command"></a>С помощью команды add-DriverGroup

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет группу драйверов на сервер.
Примеры об использовании этой команды, см. в разделе [примеры](#BKMK_examples).
## <a name="syntax"></a>Синтаксис
```
wdsutil /add-DriverGroup /DriverGroup:<Group Name>\n\
[/Server:<Server name>] [/Enabled:{Yes | No}] [/Applicability:{Matched | All}] [/Filtertype:<Filter type> /Policy:{Include | Exclude} /Value:<Value> [/Value:<Value> ...]]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ DriverGroup:<Group Name>|Указывает имя новой группы драйверов.|
|/ Server:<Server name>|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.|
|/ Enabled: {Да &#124; нет}|Включает или отключает пакета.|
|/Applicability:{Matched &#124; All}|Указывает, какие пакеты для установки при выполнении условий фильтра. **Соответствует** означает, что установка только пакетов драйверов, которые соответствуют оборудованию клиента s. **Все** означает, что установка всех пакетов на клиентах независимо от их оборудования.|
|/ Filtertype:<Filtertype>|Указывает тип фильтра, чтобы добавить в группу. В рамках одной команды можно указать несколько типов фильтров. Каждый тип фильтра может стоять **установку** и по крайней мере один **/Value**. <Filtertype> Может принимать одно из следующих:<br /><br />**BiosVendor**<br /><br />**Biosversion**<br /><br />**Тип корпуса**<br /><br />**Изготовитель**<br /><br />**UUID**<br /><br />**Версия ОС**<br /><br />**Osedition**<br /><br />**OsLanguage**<br /><br />сведения о получении значения для всех остальных типов фильтров, см. в разделе [фильтры групп драйверов](https://go.microsoft.com/fwlink/?LinkID=155158) (https://go.microsoft.com/fwlink/?LinkID=155158).|
|[/ Политики: {включают &#124; исключить}]|Указывает политику для настройки фильтра. Если **установку** присваивается **Include**, разрешено устанавливать драйверы в этой группе клиентских компьютеров, которые соответствуют заданному фильтру. Если **установку** присваивается **исключить**, а затем клиентские компьютеры, которые соответствуют заданному фильтру не разрешены для установки драйверов в этой группе.|
|[/ Value:<Value>]|Указывает значения клиента, соответствующий **/Filtertype**. Можно указать несколько значений для одного типа. См. в статье приведен список допустимых значений для определенных типов фильтра. Ниже приведены атрибуты для **Chassistype**. Сведения о получении значения для всех остальных типов фильтров, см. в разделе [фильтры групп драйверов](https://go.microsoft.com/fwlink/?LinkID=155158) (https://go.microsoft.com/fwlink/?LinkID=155158).<br /><br />**Другие**<br /><br />**UnknownChassis**<br /><br />**Настольный компьютер**<br /><br />**LowProfileDesktop**<br /><br />**PizzaBox**<br /><br />**MiniTower**<br /><br />**Башня**<br /><br />**Переносимая**<br /><br />**Ноутбук**<br /><br />**Записная книжка**<br /><br />**Handheld**<br /><br />**DockingStation**<br /><br />**AllInOne**<br /><br />**SubNotebook**<br /><br />**SpaceSaving**<br /><br />**LunchBox**<br /><br />**MainSystemChassis**<br /><br />**ExpansionChassis**<br /><br />**Дополнительный корпус**<br /><br />**BusExpansionChassis**<br /><br />**PeripheralChassis**<br /><br />**StoraeChassis**<br /><br />**RackmountChassis**<br /><br />**SealedCasecomputer**<br /><br />**MultiSystemChassis**<br /><br />**CompactPci**<br /><br />**AdvancedTca**|
## <a name="BKMK_examples"></a>Примеры
Чтобы добавить группу драйверов, введите одно из следующих:
```
wdsutil /add-DriverGroup /DriverGroup:printerdrivers /Enabled:Yes
```
```
wdsutil /add-DriverGroup /DriverGroup:printerdrivers /Applicability:All /Filtertype:Manufacturer /Policy:Include /Value:Name1 /Filtertype:Chassistype /Policy:Exclude /Value:Tower /Value:MiniTower
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add-DriverGroupPackage](using-the-add-drivergrouppackage-command.md)
[с помощью команды add-DriverGroupPackages](using-the-add-drivergrouppackages-command.md) 
 [ С помощью команды add-DriverGroupFilter](using-the-add-drivergroupfilter-command.md)
