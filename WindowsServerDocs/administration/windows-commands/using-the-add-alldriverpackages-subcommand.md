---
title: С помощью подкоманды add-AllDriverPackages
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 3f934d8c65da939fb60c564b375699f411b7c9ac
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440836"
---
# <a name="using-the-add-alldriverpackages-subcommand"></a>С помощью подкоманды add-AllDriverPackages



Добавляет все пакеты драйверов, которые хранятся в папке на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Add-AllDriverPackages /FolderPath:<Folder Path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>]
```

## <a name="parameters"></a>Параметры

|          Параметр           |                                                              Описание                                                              |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|  / FolderPath:\<путь к папке >  |                      Указывает полный путь к папке, содержащей INF-файлов для пакетов драйверов.                      |
|   [/ Server:\<имя сервера >]   | Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер. |
|     [/ Архитектура: {x86      |                                                                 IA64                                                                  |
| [/ DriverGroup:\<имя группы >] |                             Указывает имя группы драйверов, к которому следует добавить пакеты.                             |

## <a name="BKMK_examples"></a>Примеры

Чтобы добавить пакеты драйверов, введите одно из следующих:
```
WDSUTIL /verbose /Add-AllDriverPackages /FolderPath:"C:\Temp\Drivers" /Architecture:x86
```
```
WDSUTIL /Add-AllDriverPackages /FolderPath:"C:\Temp\Drivers\Printers" /DriverGroup:"Printer Drivers"
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Добавить WdsDriverPackage](https://technet.microsoft.com/library/dn283440.aspx)