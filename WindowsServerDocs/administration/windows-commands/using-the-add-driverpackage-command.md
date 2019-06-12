---
title: С помощью команды add-DriverPackage
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ac9e8d5-63ec-4ce8-86fc-85d28011050b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 893bcd3b28aaa5d501017fe65b7b5205e9452693
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440689"
---
# <a name="using-the-add-driverpackage-command"></a>С помощью команды add-DriverPackage



Добавляет пакет драйверов на сервер.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Add-DriverPackage /InfFile:<Inf File path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>] [/Name:<Friendly Name>]
```

## <a name="parameters"></a>Параметры

|          Параметр           |                                                              Описание                                                              |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|   INF-файл:\<путь к INF-файла >   |                                           Указывает полный путь к INF-файл для добавления.                                            |
|    / Server:\<имя сервера >    | Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер. |
|      / Архитектура: {x86      |                                                                 IA64                                                                  |
| [/ DriverGroup:\<имя группы >] |                             Указывает имя группы драйверов, в которую должен быть добавлен пакет.                              |
|   [/ Name:\<понятное имя >]   |                                           Указывает понятное имя для пакета драйверов.                                            |

## <a name="BKMK_examples"></a>Примеры

Чтобы добавить пакет драйвера, введите одно из следующих:
```
WDSUTIL /verbose /Add-DriverPackage /InfFile:"C:\Temp\Display.inf"
```
```
WDSUTIL /Add-DriverPackage /Server:MyWDSServer /InfFile:"C:\Temp\Display.inf" /Architecture:x86 /DriverGroup:x86Drivers /Name:"Display Driver"
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

