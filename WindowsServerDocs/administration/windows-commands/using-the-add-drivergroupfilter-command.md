---
title: С помощью команды add-DriverGroupFilter
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a66c5e68-99ea-4e47-b68d-8109633ae336
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 16962bd87fabd1ee689b962547c2b1aa470283c1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817385"
---
# <a name="using-the-add-drivergroupfilter-command"></a>С помощью команды add-DriverGroupFilter



Добавление фильтра к группе драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Add-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type> /Policy:{Include | Exclude} /Value:<Value> [/Value:<Value> ...]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/ DriverGroup:\<имя группы >|Задает имя группы драйверов.|
|[/ Server:\<имя сервера >]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.|
|/ FilterType:\<FilterType >|Указывает тип фильтра, чтобы добавить в группу. В рамках одной команды можно указать несколько типов фильтров. Каждый тип фильтра может стоять **установку** и включать по крайней мере один **/Value**. \<FilterType > может быть **BiosVendor**, **BiosVersion**, **ChassisType**, **производителя**, **Uuid**, **OsVersion**, **OsEdition**, или **OsLanguage**. Сведения о получении значения для всех остальных типов фильтров, см. в разделе [фильтры групп драйверов](https://go.microsoft.com/fwlink/?LinkID=155158) (https://go.microsoft.com/fwlink/?LinkID=155158).|
|[/ Политики: {включают | Исключить}]|Если **установку** присваивается **Include**, разрешено устанавливать драйверы в этой группе клиентских компьютеров, которые соответствуют заданному фильтру. Если **установку** присваивается **исключить**, клиентские компьютеры, которые соответствуют заданному фильтру не разрешены для установки драйверов в этой группе.|
|[/ Value:\<значение >]|Указывает значения клиента, соответствующий **/FilterType**. Можно указать несколько значений для одного типа. Ниже приведен список допустимых значений для **ChassisType**. Сведения о получении значения для всех остальных типов фильтров, см. в разделе [фильтры групп драйверов](https://go.microsoft.com/fwlink/?LinkID=155158) (https://go.microsoft.com/fwlink/?LinkID=155158).</br>**Другие**</br>**UnknownChassis**</br>**Настольный компьютер**</br>**LowProfileDesktop**</br>**PizzaBox**</br>**MiniTower**</br>**Башня**</br>**Переносимая**</br>**Ноутбук**</br>**Записная книжка**</br>**Handheld**</br>**DockingStation**</br>**AllInOne**</br>**SubNotebook**</br>**SpaceSaving**</br>**LunchBox**</br>**MainSystemChassis**</br>**ExpansionChassis**</br>**Дополнительный корпус**</br>**BusExpansionChassis**</br>**PeripheralChassis**</br>**StorageChassis**</br>**RackMountChassis**</br>**SealedCaseComputer**</br>**MultiSystemChassis**</br>**CompactPci**</br>**AdvancedTca**|

## <a name="BKMK_examples"></a>Примеры

Чтобы добавить фильтр к группе драйверов, введите одно из следующих:
```
WDSUTIL /Add-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /Value:Name1 /Value:Name2
```
```
WDSUTIL /Add-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /Value:Name1 /FilterType:ChassisType /Policy:Exclude /Value:Tower /Value:MiniTower
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

