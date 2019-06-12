---
title: С помощью команды add-DriverGroupPackage
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7cd323ae-9049-448e-a460-6c7d6462d4c8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ad9d180e2cf2110d36ebc82211af3a495a0e0b6b
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440731"
---
# <a name="using-the-add-drivergrouppackage-command"></a>С помощью команды add-DriverGroupPackage

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет группу драйверов пакет драйверов.
## <a name="syntax"></a>Синтаксис
```
wdsutil /add-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```
## <a name="parameters"></a>Параметры

|         Параметр         |                                                                                                                                               Описание                                                                                                                                               |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| / DriverGroup:<Group Name> |                                                                                                                                 Задает имя группы драйверов.                                                                                                                                 |
|   / Server:<Server name>   |                                                                                  Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.                                                                                  |
|   / DriverPackage:<Name>   |                                                                      Указывает имя пакета драйвера для добавления в группу. Необходимо указать этот параметр, если пакет драйверов не может быть однозначно идентифицируется по имени.                                                                       |
|      / PackageId:<ID>      | Указывает идентификатор для пакета. Чтобы найти идентификатор пакета, щелкните группу драйверов, в который входит пакет (или **все пакеты** узла), щелкните правой кнопкой мыши пакет и нажмите кнопку **свойства**. Идентификатор пакета указан на **Общие** вкладку, например: **{DD098D20-1850-4fc8-8E35-EA24A1BEFF5E}** . |

## <a name="BKMK_examples"></a>Примеры
Чтобы добавить пакет драйвера, введите одно из следующих:
```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```
```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /DriverPackage:XYZ
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add-DriverGroupPackages](using-the-add-drivergrouppackages-command.md)
[с помощью команды add-DriverPackage](using-the-add-driverpackage-command.md) 
 [Помощью add-AllDriverPackages подкоманды](using-the-add-alldriverpackages-subcommand.md)
