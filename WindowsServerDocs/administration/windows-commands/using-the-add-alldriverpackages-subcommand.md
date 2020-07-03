---
title: Использование подкоманды Add-Аллдриверпаккажес
description: Справочная статья по Add-Аллдриверпаккажес, которая добавляет все пакеты драйверов, которые хранятся в папке на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ba6641c1-d7e9-43a9-9819-702dad5484ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a505175b1b2efc56c9be6d77384c71f8c1db7392
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85937259"
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
|  FolderPath\<Folder Path>  |                      Указывает полный путь к папке, содержащей INF-файлы для пакетов драйверов.                      |
|   [/Server: \<Server name> ]   | Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер. |
|     [/Арчитектуре: {x86      |                                                                 ia64                                                                  |
| [/Дриверграуп: \<Group Name> ] |                             Указывает имя группы драйверов, в которую должны быть добавлены пакеты.                             |

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