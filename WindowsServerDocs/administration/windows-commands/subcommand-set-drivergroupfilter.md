---
title: Подкоманды DriverGroupFilter набора
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 829ab1f0-4514-421e-9cc0-767b238da69c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5423b6e7444c01c5889a5b207a545d1761a73402
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66441147"
---
# <a name="subcommand-set-drivergroupfilter"></a>Подкоманда: set-DriverGroupFilter



Добавляет или удаляет существующий фильтр группа драйверов из группы драйверов.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Set-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type> [/Policy:{Include | Exclude}] [/AddValue:<Value> [/AddValue:<Value> ...]] [/RemoveValue:<Value> [/RemoveValue:<Value> ...]]
```

## <a name="parameters"></a>Параметры

|         Параметр          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Описание                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| / DriverGroup:\<имя группы > |                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Задает имя группы драйверов.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|  [/ Server:\<имя сервера >]  |                                                                                                                                                                                                                                                                                                                                                                                                                Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| / FilterType:\<FilterType >  |                                                                                                                                                                                                                                                                       Указывает тип фильтра группы драйверов для добавления или удаления. Можно указать несколько фильтров в рамках одной команды. Для каждого **/FilterType**, можно добавить или удалить несколько значений, используя **/RemoveValue** и **/AddValue**. \<FilterType > может принимать одно из следующих:</br>**BiosVendor**</br>**BiosVersion**</br>**Тип корпуса**</br>**Изготовитель**</br>**UUID**</br>**версия ОС**</br>**OsEdition**</br>**OsLanguage**                                                                                                                                                                                                                                                                        |
|     [/ Политики: {включают      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Исключить}]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|    [/ AddValue:\<значение >]    | Указывает новое значение клиента, чтобы добавить в фильтр. Можно указать несколько значений для типа один фильтр. Ниже приведен список для допустимые значения атрибута для **ChassisType**. Сведения о получении значения для всех остальных типов фильтров, см. в разделе [фильтры групп драйверов](https://go.microsoft.com/fwlink/?LinkID=155158) (<https://go.microsoft.com/fwlink/?LinkID=155158>).</br>**Другие**</br>**UnknownChassis**</br>**Настольный компьютер**</br>**LowProfileDesktop**</br>**PizzaBox**</br>**MiniTower**</br>**Башня**</br>**Переносимая**</br>**Ноутбук**</br>**Записная книжка**</br>**Handheld**</br>**DockingStation**</br>**AllInOne**</br>**SubNotebook**</br>**SpaceSaving**</br>**LunchBox**</br>**MainSystemChassis**</br>**ExpansionChassis**</br>**Дополнительный корпус**</br>**BusExpansionChassis**</br>**PeripheralChassis**</br>**StorageChassis**</br>**RackMountChassis**</br>**SealedCaseComputer**</br>**MultiSystemChassis**</br>**CompactPci**</br>**AdvancedTca** |
|  [/ RemoveValue:\<значение >]   |                                                                                                                                                                                                                                                                                                                                                                                                                                     Указывает значение существующего клиента, удален из текущего фильтра, так как указан с **/AddValue**.                                                                                                                                                                                                                                                                                                                                                                                                                                      |

## <a name="BKMK_examples"></a>Примеры

Чтобы удалить фильтр, введите одно из следующих:
```
WDSUTIL /Set-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /AddValue:Name1 /RemoveValue:Name2
```
```
WDSUTIL /Set-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /RemoveValue:Name1 /FilterType:ChassisType /Policy:Exclude /AddValue:Tower /AddValue:MiniTower
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)