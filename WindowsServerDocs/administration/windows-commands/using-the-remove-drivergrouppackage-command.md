---
title: Использование команды Remove-Дриверграуппаккаже
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e48616d-d6a4-45f0-a5c6-efe62bf6a0ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 122f82b22fd72dc09d4703552cb7b6ac5662aa07
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362902"
---
# <a name="using-the-remove-drivergrouppackage-command"></a>Использование команды Remove-Дриверграуппаккаже



Удаляет пакет драйвера из группы драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[/Server:\<имя сервера >]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|
|[/Дриверпаккаже:\<имя >]|Указывает имя удаляемого пакета драйверов.|
|[/Паккажеид: идентификатор\<>]|Указывает идентификатор служб развертывания Windows для удаляемого пакета драйверов. Этот параметр необходимо указать, если пакет драйверов не может быть однозначно идентифицирован по имени.|

## <a name="BKMK_examples"></a>Примеров

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /DriverPackage:XYZ
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)