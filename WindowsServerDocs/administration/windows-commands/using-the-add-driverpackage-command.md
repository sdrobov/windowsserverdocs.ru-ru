---
title: Add-Дриверпаккаже
description: Раздел команд Windows для Add-Дриверпаккаже, который добавляет пакет драйверов на сервер.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ac9e8d5-63ec-4ce8-86fc-85d28011050b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e2ccdfcddd2f605eccd9cd32fed7b8c6921297fc
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832017"
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
|   Инффиле:\<путь к файлу INF >   |                                           Указывает полный путь к добавляемому INF-файлу.                                            |
|    /Server: имя сервера\<>    | Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер. |
|      /Арчитектуре: {x86      |                                                                 ia64                                                                  |
| [/Дриверграуп: имя группы\<>] |                             Указывает имя группы драйверов, в которую должен быть добавлен пакет.                              |
|   [/Name:\<понятное имя >]   |                                           Указывает понятное имя для пакета драйверов.                                            |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы добавить пакет драйвера, введите один из следующих элементов:
```
WDSUTIL /verbose /Add-DriverPackage /InfFile:C:\Temp\Display.inf
```
```
WDSUTIL /Add-DriverPackage /Server:MyWDSServer /InfFile:C:\Temp\Display.inf /Architecture:x86 /DriverGroup:x86Drivers /Name:Display Driver
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

