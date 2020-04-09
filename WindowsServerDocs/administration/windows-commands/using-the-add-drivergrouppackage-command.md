---
title: Add-Дриверграуппаккаже
description: Раздел команд Windows для Add-Дриверграуппаккаже, который добавляет пакет драйверов в группу драйверов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7cd323ae-9049-448e-a460-6c7d6462d4c8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6753baeb03b99ee149250d41844469a5008f5ecd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832077"
---
# <a name="add-drivergrouppackage"></a>Add-Дриверграуппаккаже

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет пакет драйверов в группу драйверов.

## <a name="syntax"></a>Синтаксис
```
wdsutil /add-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```
### <a name="parameters"></a>Параметры

|         Параметр         |                                                                                                                                               Описание                                                                                                                                               |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /Дриверграуп:<Group Name> |                                                                                                                                 Указывает имя группы драйверов.                                                                                                                                 |
|   /Server:<Server name>   |                                                                                  Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.                                                                                  |
|   /Дриверпаккаже:<Name>   |                                                                      Указывает имя пакета драйверов, добавляемого в группу. Этот параметр необходимо указать, если пакет драйверов не может быть однозначно идентифицирован по имени.                                                                       |
|      /Паккажеид:<ID>      | Указывает идентификатор пакета. Чтобы найти идентификатор пакета, щелкните группу драйверов, в которой находится пакет (или узел **все пакеты** ), щелкните правой кнопкой мыши пакет и выберите пункт **свойства**. Идентификатор пакета указан на вкладке **Общие** , например: **{DD098D20-1850-4fc8-8E35-EA24A1BEFF5E}** . |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы добавить пакет драйвера, введите один из следующих элементов:
```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```
```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /DriverPackage:XYZ
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[помощью команды Add-Дриверграуппаккажес](using-the-add-drivergrouppackages-command.md) ,
[помощью](using-the-add-driverpackage-command.md) команды Add-дриверпаккаже,
[с помощью подкоманды Add-аллдриверпаккажес](using-the-add-alldriverpackages-subcommand.md) .
