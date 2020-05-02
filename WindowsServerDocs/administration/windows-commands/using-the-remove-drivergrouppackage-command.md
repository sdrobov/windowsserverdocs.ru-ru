---
title: Remove-Дриверграуппаккаже
description: Справочный раздел по Remove-Дриверграуппаккаже, который удаляет пакет драйверов из группы драйверов на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2e48616d-d6a4-45f0-a5c6-efe62bf6a0ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c63c6ef0ed9af49506d80a715f23111bfd62070f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720404"
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
|[/Server:\<имя сервера>]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|
|[/Дриверпаккаже:\<Name>]|Указывает имя удаляемого пакета драйверов.|
|[/Паккажеид:\<ID>]|Указывает идентификатор служб развертывания Windows для удаляемого пакета драйверов. Этот параметр необходимо указать, если пакет драйверов не может быть однозначно идентифицирован по имени.|

## <a name="examples"></a>Примеры

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /DriverPackage:XYZ
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)