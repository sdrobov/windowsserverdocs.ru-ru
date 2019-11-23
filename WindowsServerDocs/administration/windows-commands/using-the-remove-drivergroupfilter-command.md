---
title: Использование команды Remove-Дриверграупфилтер
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 837bd5d4-c79d-4714-942d-9875bd8e61dc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 75b4a1446b5fb4db4132a39b6e5ba70cd1c4ab4b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362925"
---
# <a name="using-the-remove-drivergroupfilter-command"></a>Использование команды Remove-Дриверграупфилтер



Удаляет правило фильтрации из группы драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/Дриверграуп: имя группы\<>|Указывает имя группы драйверов.|
|[/Server:\<имя сервера >]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|
|[/Филтертипе:\<FilterType >]|Указывает тип фильтра, удаляемого из группы. \<FilterType > может быть одним из следующих:</br>**биосвендор**</br>**биосверсион**</br>**чассистипе**</br>**Производителя**</br>**UUID**</br>**OsVersion**</br>**оседитион**</br>**ослангуаже**|

## <a name="BKMK_examples"></a>Примеров

Чтобы удалить фильтр, введите один из следующих элементов:
```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer
```
```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /FilterType:OSLanguage
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)