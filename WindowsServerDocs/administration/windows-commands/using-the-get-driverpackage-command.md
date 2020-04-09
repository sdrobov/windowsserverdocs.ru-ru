---
title: Get-Дриверпаккаже
description: Раздел команд Windows для Get-Дриверпаккаже, который отображает сведения о пакете драйверов на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 94d231e4-ff01-48e7-9bc8-7b0d97a4339e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1906a109d22b24b5a44227d56c726996e6532bd6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831057"
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
| [/Server:\<имя сервера >] |              Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.               |
| [/Дриверпаккаже:\<имя >] |                                                        Указывает имя пакета драйверов для отображения.                                                         |
|    [/Паккажеид: идентификатор\<>]    | Указывает идентификатор служб развертывания Windows для отображаемого пакета драйверов. Если пакет драйвера не может быть однозначно идентифицирован по имени, необходимо указать идентификатор. |
|     [/Show: {Drivers     |                                                                              Файлы                                                                               |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы просмотреть сведения о пакете драйвера, введите одно из следующих действий:
```
WDSUTIL /Get-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Get-DriverPackage /DriverPackage:MyDriverPackage /Show:All
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)