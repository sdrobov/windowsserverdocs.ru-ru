---
title: Add-Дриверпаккаже
description: Справочный раздел по Add-Дриверпаккаже, который добавляет пакет драйверов на сервер.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ac9e8d5-63ec-4ce8-86fc-85d28011050b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 12d7f7078cf3dde10f834a4d4c7784ecc1d9bdf2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721095"
---
# <a name="add-driverpackage"></a>Add-Дриверпаккаже

Добавляет пакет драйверов на сервер.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Add-DriverPackage /InfFile:<Inf File path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>] [/Name:<Friendly Name>]
```

### <a name="parameters"></a>Параметры

|          Параметр           |                                                              Описание                                                              |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|   Инффиле:\<путь к INF-файлу>   |                                           Указывает полный путь к добавляемому INF-файлу.                                            |
|    /Server:\<имя сервера>    | Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер. |
|      /Арчитектуре: {x86      |                                                                 ia64                                                                  |
| [/Дриверграуп:\<имя группы>] |                             Указывает имя группы драйверов, в которую должен быть добавлен пакет.                              |
|   [/Name:\<понятное имя>]   |                                           Указывает понятное имя для пакета драйверов.                                            |

## <a name="examples"></a>Примеры

Чтобы добавить пакет драйвера, введите один из следующих элементов:
```
WDSUTIL /verbose /Add-DriverPackage /InfFile:C:\Temp\Display.inf
```
```
WDSUTIL /Add-DriverPackage /Server:MyWDSServer /InfFile:C:\Temp\Display.inf /Architecture:x86 /DriverGroup:x86Drivers /Name:Display Driver
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

