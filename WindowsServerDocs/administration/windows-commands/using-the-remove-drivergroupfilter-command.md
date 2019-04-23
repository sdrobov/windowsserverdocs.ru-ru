---
title: С помощью команды remove-DriverGroupFilter
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: a546ead7220273955368c582ac1e3f9b3f61c191
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59883435"
---
# <a name="using-the-remove-drivergroupfilter-command"></a>С помощью команды remove-DriverGroupFilter



Удаляет правила фильтрации из группы драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/ DriverGroup:\<имя группы >|Задает имя группы драйверов.|
|[/ Server:\<имя сервера >]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.|
|[/ FilterType:\<FilterType >]|Указывает тип фильтра, чтобы удалить из группы. \<FilterType > может принимать одно из следующих:</br>**BiosVendor**</br>**BiosVersion**</br>**Тип корпуса**</br>**Изготовитель**</br>**UUID**</br>**версия ОС**</br>**OsEdition**</br>**OsLanguage**|

## <a name="BKMK_examples"></a>Примеры

Чтобы удалить фильтр, введите одно из следующих:
```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer
```
```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /FilterType:OSLanguage
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)