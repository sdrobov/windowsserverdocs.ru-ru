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
ms.openlocfilehash: 6574177f1f0a8ead0cc2fa596380eb2c980f8d1f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59888525"
---
# <a name="using-the-get-driverpackage-command"></a>С помощью команды get-DriverPackage



Отображает сведения о пакете драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Get-DriverPackage [/Server:<Server name>] {/DriverPackage:<Package Name> | /PackageId:<ID>} [/Show:{Drivers | Files | All}]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[/ Server:\<имя сервера >]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.|
|[/ DriverPackage:\<имя >]|Указывает имя пакета драйверов для отображения.|
|[/ PackageId:\<идентификатор >]|Указывает идентификатор служб развертывания Windows из пакета драйверов для отображения. Если пакет драйверов не может быть однозначно идентифицируется по имени, необходимо указать идентификатор.|
|[/ Show: {драйверы | Файлы | Все}]|Указывает, какие сведения для отображения (Если указано). Если **/Показать** не указан, по умолчанию используется для возвращения только драйвер метаданных пакета. **Драйверы** отображаются все драйверы в пакете. **Файлы** отображает список файлов в пакете. **Все** отображаются драйверы, файлы и метаданные.|

## <a name="BKMK_examples"></a>Примеры

Чтобы просмотреть сведения о пакете драйверов, введите одно из следующих:
```
WDSUTIL /Get-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Get-DriverPackage /DriverPackage:MyDriverPackage /Show:All
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)