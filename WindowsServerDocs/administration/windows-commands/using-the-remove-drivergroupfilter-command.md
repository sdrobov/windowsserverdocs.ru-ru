---
title: Remove-Дриверграупфилтер
description: Справочный раздел по Remove-Дриверграупфилтер, который удаляет правило фильтра из группы драйверов на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 837bd5d4-c79d-4714-942d-9875bd8e61dc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dd6fcbc8f87539ac687927b9e58ed15edb524ef6
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720412"
---
# <a name="remove-drivergroupfilter"></a>Remove-Дриверграупфилтер



Удаляет правило фильтрации из группы драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/Дриверграуп:\<имя группы>|Указывает имя группы драйверов.|
|[/Server:\<имя сервера>]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|
|[/Филтертипе:\<FilterType>]|Указывает тип фильтра, удаляемого из группы. \<FilterType> может быть одним из следующих:</br>**биосвендор**</br>**биосверсион**</br>**ChassisType**</br>**Изготовитель**</br>**UUID**</br>**OsVersion**</br>**оседитион**</br>**ослангуаже**|

## <a name="examples"></a>Примеры

Чтобы удалить фильтр, введите один из следующих элементов:
```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer
```
```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /FilterType:OSLanguage
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)