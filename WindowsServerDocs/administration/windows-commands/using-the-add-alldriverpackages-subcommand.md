---
title: Использование подкоманды Add-Аллдриверпаккажес
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ba6641c1-d7e9-43a9-9819-702dad5484ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d8290a95dd53718b200d10b6804d312abe95e257
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363886"
---
# <a name="using-the-add-alldriverpackages-subcommand"></a>Использование подкоманды Add-Аллдриверпаккажес



Добавляет все пакеты драйверов, хранящиеся в папке, на сервер.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Add-AllDriverPackages /FolderPath:<Folder Path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>]
```

## <a name="parameters"></a>Параметры

|          Параметр           |                                                              Описание                                                              |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|  /Фолдерпас: путь к папке\<>  |                      Указывает полный путь к папке, содержащей INF-файлы для пакетов драйверов.                      |
|   [/Server:\<имя сервера >]   | Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер. |
|     [/Арчитектуре: {x86      |                                                                 ia64                                                                  |
| [/Дриверграуп: имя группы\<>] |                             Указывает имя группы драйверов, в которую должны быть добавлены пакеты.                             |

## <a name="BKMK_examples"></a>Примеров

Чтобы добавить пакеты драйверов, введите один из следующих элементов:
```
WDSUTIL /verbose /Add-AllDriverPackages /FolderPath:"C:\Temp\Drivers" /Architecture:x86
```
```
WDSUTIL /Add-AllDriverPackages /FolderPath:"C:\Temp\Drivers\Printers" /DriverGroup:"Printer Drivers"
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Add-Вдсдриверпаккаже](https://technet.microsoft.com/library/dn283440.aspx)