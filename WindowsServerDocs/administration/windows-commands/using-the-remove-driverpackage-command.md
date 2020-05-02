---
title: Remove-Дриверпаккаже
description: Справочный раздел по Remove-Дриверпаккаже, который удаляет пакет драйверов с сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6b201e91-0d44-4e4a-8252-8b0235df1002
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 623fa7bb22c4aa4e545156cf0b214a4042fb90a3
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720385"
---
# <a name="remove-driverpackage"></a>Remove-Дриверпаккаже

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 

Удаляет пакет драйвера с сервера.

## <a name="syntax"></a>Синтаксис
```
wdsutil /remove-DriverPackage [/Server:<Server name>] {/DriverPackage:<Package Name> | /PackageId:<ID>}
```
### <a name="parameters"></a>Параметры

|        Параметр        |                                                                            Описание                                                                             |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server:<Server name>] |              Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.              |
| [/Дриверпаккаже:<Name>] |                                                        Указывает имя удаляемого пакета драйверов.                                                         |
|    [/Паккажеид:<ID>]    | Указывает идентификатор служб развертывания Windows для удаляемого пакета драйверов. Если пакет драйвера не может быть однозначно идентифицирован по имени, необходимо указать идентификатор. |

## <a name="examples"></a>Примеры
Чтобы просмотреть сведения об образах, введите одно из следующих действий:
```
wdsutil /remove-DriverPackage /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```
```
wdsutil /remove-DriverPackage /Server:MyWdsServer /DriverPackage:MyDriverPackage
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды Remove-дриверпаккажес](using-the-remove-driverpackages-command.md)
