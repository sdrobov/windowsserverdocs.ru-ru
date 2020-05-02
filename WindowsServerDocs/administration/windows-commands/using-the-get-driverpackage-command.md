---
title: Get-Дриверпаккаже
description: Справочный раздел по Get-Дриверпаккаже, который отображает сведения о пакете драйверов на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 94d231e4-ff01-48e7-9bc8-7b0d97a4339e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4fc6bc327b46f8219a7c40fa47e85cc94b6fc749
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719936"
---
# <a name="get-driverpackage"></a>Get-Дриверпаккаже

Отображает сведения о пакете драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Get-DriverPackage [/Server:<Server name>] {/DriverPackage:<Package Name> | /PackageId:<ID>} [/Show:{Drivers | Files | All}]
```

### <a name="parameters"></a>Параметры

|        Параметр         |                                                                           Описание                                                                            |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server:\<имя сервера>] |              Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.               |
| [/Дриверпаккаже:\<Name>] |                                                        Указывает имя пакета драйверов для отображения.                                                         |
|    [/Паккажеид:\<ID>]    | Указывает идентификатор служб развертывания Windows для отображаемого пакета драйверов. Если пакет драйвера не может быть однозначно идентифицирован по имени, необходимо указать идентификатор. |
|     [/Show: {Drivers     |                                                                              Файлы                                                                               |

## <a name="examples"></a>Примеры

Чтобы просмотреть сведения о пакете драйвера, введите одно из следующих действий:
```
WDSUTIL /Get-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Get-DriverPackage /DriverPackage:MyDriverPackage /Show:All
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)