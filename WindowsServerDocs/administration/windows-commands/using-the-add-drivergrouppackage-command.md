---
title: Add-Дриверграуппаккаже
description: Справочный раздел по Add-Дриверграуппаккаже, который добавляет пакет драйверов в группу драйверов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7cd323ae-9049-448e-a460-6c7d6462d4c8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4baf4f16740e65c432cc09ca24270ab479346ac2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721111"
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
- [Ключ](command-line-syntax-key.md)
синтаксиса командной строки[с помощью команды](using-the-add-drivergrouppackages-command.md)
Add-дриверграуппаккажес с помощью команды Add-[дриверпаккаже](using-the-add-driverpackage-command.md)
[с использованием подкоманды Add-аллдриверпаккажес](using-the-add-alldriverpackages-subcommand.md) .
