---
title: С помощью команды remove-DriverPackage
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b201e91-0d44-4e4a-8252-8b0235df1002
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 217ff23b8724464670520d0b2d5b196df5a4af47
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440299"
---
# <a name="using-the-remove-driverpackage-command"></a>С помощью команды remove-DriverPackage

> Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012
> 
> 
> Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет пакет драйверов с сервера.
## <a name="syntax"></a>Синтаксис
```
wdsutil /remove-DriverPackage [/Server:<Server name>] {/DriverPackage:<Package Name> | /PackageId:<ID>}
```
## <a name="parameters"></a>Параметры

|        Параметр        |                                                                            Описание                                                                             |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/ Server:<Server name>] |              Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.              |
| [/ DriverPackage:<Name>] |                                                        Указывает имя пакета драйверов для удаления.                                                         |
|    [/ PackageId:<ID>]    | Указывает идентификатор служб развертывания Windows из пакета драйверов для удаления. Если пакет драйверов не может быть однозначно идентифицируется по имени, необходимо указать идентификатор. |

## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть сведения об образах, введите одно из следующих:
```
wdsutil /remove-DriverPackage /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```
```
wdsutil /remove-DriverPackage /Server:MyWdsServer /DriverPackage:MyDriverPackage
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды remove-DriverPackages](using-the-remove-driverpackages-command.md)
