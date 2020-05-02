---
title: Использование подкоманды Add-Аллдриверпаккажес
description: Справочный раздел по Add-Аллдриверпаккажес, который добавляет все пакеты драйверов, хранящиеся в папке, на сервер.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ba6641c1-d7e9-43a9-9819-702dad5484ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 31daa8fc3e3304dba5079672ea4619fd085dd74f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721160"
---
# <a name="add-alldriverpackages"></a>Add-Аллдриверпаккажес

Добавляет все пакеты драйверов, хранящиеся в папке, на сервер.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Add-AllDriverPackages /FolderPath:<Folder Path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>]
```

### <a name="parameters"></a>Параметры

|          Параметр           |                                                              Описание                                                              |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|  /Фолдерпас:\<путь к папке>  |                      Указывает полный путь к папке, содержащей INF-файлы для пакетов драйверов.                      |
|   [/Server:\<имя сервера>]   | Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер. |
|     [/Арчитектуре: {x86      |                                                                 ia64                                                                  |
| [/Дриверграуп:\<имя группы>] |                             Указывает имя группы драйверов, в которую должны быть добавлены пакеты.                             |

## <a name="examples"></a>Примеры

Чтобы добавить пакеты драйверов, введите один из следующих элементов:
```
WDSUTIL /verbose /Add-AllDriverPackages /FolderPath:C:\Temp\Drivers /Architecture:x86
```
```
WDSUTIL /Add-AllDriverPackages /FolderPath:C:\Temp\Drivers\Printers /DriverGroup:Printer Drivers
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Add-Вдсдриверпаккаже](https://technet.microsoft.com/library/dn283440.aspx)