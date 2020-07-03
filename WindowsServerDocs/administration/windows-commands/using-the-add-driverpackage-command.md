---
title: Add-Дриверпаккаже
description: Справочная статья по Add-Дриверпаккаже, которая добавляет пакет драйверов на сервер.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ac9e8d5-63ec-4ce8-86fc-85d28011050b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2cc253785c0a869ebf1e3f820429564eacdb2dcb
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935837"
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
|   Инффиле:\<Inf File path>   |                                           Указывает полный путь к добавляемому INF-файлу.                                            |
|    Сервером\<Server name>    | Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер. |
|      /Арчитектуре: {x86      |                                                                 ia64                                                                  |
| [/Дриверграуп: \<Group Name> ] |                             Указывает имя группы драйверов, в которую должен быть добавлен пакет.                              |
|   [/Name: \<Friendly Name> ]   |                                           Указывает понятное имя для пакета драйверов.                                            |

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

