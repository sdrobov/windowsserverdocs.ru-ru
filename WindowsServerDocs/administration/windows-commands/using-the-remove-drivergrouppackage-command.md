---
title: С помощью команды remove-DriverGroupPackage
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 82a8fb8fbe9e713c3e22c08839bc4bc22fe900db
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59883995"
---
# <a name="using-the-remove-drivergrouppackage-command"></a>С помощью команды remove-DriverGroupPackage



Удаляет пакет драйверов из группы драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[/ Server:\<имя сервера >]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.|
|[/ DriverPackage:\<имя >]|Указывает имя пакета драйверов для удаления.|
|[/ PackageId:\<идентификатор >]|Указывает идентификатор служб развертывания Windows из пакета драйверов для удаления. Необходимо указать этот параметр, если пакет драйверов не может быть однозначно идентифицируется по имени.|

## <a name="BKMK_examples"></a>Примеры

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /DriverPackage:XYZ
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)