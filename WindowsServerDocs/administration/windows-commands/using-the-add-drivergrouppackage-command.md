---
title: Add-Дриверграуппаккаже
description: Справочная статья по Add-Дриверграуппаккаже, которая добавляет пакет драйверов в группу драйверов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7cd323ae-9049-448e-a460-6c7d6462d4c8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5782fe849669619bf46426ad698866c05007e426
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85937209"
---
# <a name="add-drivergrouppackage"></a>Add-Дриверграуппаккаже

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет пакет драйверов в группу драйверов.

## <a name="syntax"></a>Синтаксис
```
wdsutil /add-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```
### <a name="parameters"></a>Параметры

|         Параметр         |                                                                                                                                               Описание                                                                                                                                               |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /Дриверграуп:<Group Name> |                                                                                                                                 Указывает имя группы драйверов.                                                                                                                                 |
|   Сервером<Server name>   |                                                                                  Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.                                                                                  |
|   /Дриверпаккаже:<Name>   |                                                                      Указывает имя пакета драйверов, добавляемого в группу. Этот параметр необходимо указать, если пакет драйверов не может быть однозначно идентифицирован по имени.                                                                       |
|      PackageId<ID>      | Указывает идентификатор пакета. Чтобы найти идентификатор пакета, щелкните группу драйверов, в которой находится пакет (или узел **все пакеты** ), щелкните правой кнопкой мыши пакет и выберите пункт **свойства**. Идентификатор пакета указан на вкладке **Общие** , например: **{DD098D20-1850-4fc8-8E35-EA24A1BEFF5E}**. |

## <a name="examples"></a>Примеры
Чтобы добавить пакет драйвера, введите один из следующих элементов:
```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```
```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /DriverPackage:XYZ
```
## <a name="additional-references"></a>Дополнительные ссылки
- Ключ синтаксиса [командной строки](command-line-syntax-key.md) 
 [Использование команды](using-the-add-drivergrouppackages-command.md) 
 Add-дриверграуппаккажес [Использование команды](using-the-add-driverpackage-command.md) 
 Add-дриверпаккаже [Использование подкоманды Add-аллдриверпаккажес](using-the-add-alldriverpackages-subcommand.md)
