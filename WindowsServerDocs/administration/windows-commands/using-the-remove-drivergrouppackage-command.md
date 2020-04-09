---
title: Remove-Дриверграуппаккаже
description: Раздел команд Windows для Remove-Дриверграуппаккаже, который удаляет пакет драйверов из группы драйверов на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2e48616d-d6a4-45f0-a5c6-efe62bf6a0ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9dd30f430bd91bf2680cd1138270526bce965f9d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830467"
---
# <a name="remove-drivergrouppackage"></a>Remove-Дриверграуппаккаже



Удаляет пакет драйвера из группы драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[/Server:\<имя сервера >]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|
|[/Дриверпаккаже:\<имя >]|Указывает имя удаляемого пакета драйверов.|
|[/Паккажеид: идентификатор\<>]|Указывает идентификатор служб развертывания Windows для удаляемого пакета драйверов. Этот параметр необходимо указать, если пакет драйверов не может быть однозначно идентифицирован по имени.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /DriverPackage:XYZ
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)