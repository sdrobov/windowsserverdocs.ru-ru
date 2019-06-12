---
title: С помощью команды get-DriverPackage
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 94d231e4-ff01-48e7-9bc8-7b0d97a4339e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b0f123d281625140b3c4ba46316cb9b773bf5fee
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440516"
---
# <a name="using-the-get-driverpackage-command"></a>С помощью команды get-DriverPackage



Отображает сведения о пакете драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Get-DriverPackage [/Server:<Server name>] {/DriverPackage:<Package Name> | /PackageId:<ID>} [/Show:{Drivers | Files | All}]
```

## <a name="parameters"></a>Параметры

|        Параметр         |                                                                           Описание                                                                            |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/ Server:\<имя сервера >] |              Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.               |
| [/ DriverPackage:\<имя >] |                                                        Указывает имя пакета драйверов для отображения.                                                         |
|    [/ PackageId:\<идентификатор >]    | Указывает идентификатор служб развертывания Windows из пакета драйверов для отображения. Если пакет драйверов не может быть однозначно идентифицируется по имени, необходимо указать идентификатор. |
|     [/ Show: {драйверы     |                                                                              Файлы                                                                               |

## <a name="BKMK_examples"></a>Примеры

Чтобы просмотреть сведения о пакете драйверов, введите одно из следующих:
```
WDSUTIL /Get-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Get-DriverPackage /DriverPackage:MyDriverPackage /Show:All
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)