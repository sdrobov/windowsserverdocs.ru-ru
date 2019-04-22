---
title: Подкоманды DriverPackage набора
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 11804bb6-ca29-4461-8c63-5131748cd742
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0513d3de2416f93f69b1e1cc286c38b12be94d15
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59818825"
---
# <a name="subcommand-set-driverpackage"></a>Подкоманда: set-DriverPackage



Переименовывает и/или включает или отключает пакет драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Set-DriverPackage [/Server:<Server name>] {/DriverPackage:<Name> | /PackageId:<ID>} [/Name:<New Name>] [/Enabled:{Yes | No}
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[/ Server:\<имя сервера >]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.|
|[/ DriverPackage:\<имя >]|Указывает текущее имя пакета драйверов для изменения.|
|[/ PackageId:\<идентификатор >]|Указывает идентификатор службы развертывания Windows из пакета драйверов. Необходимо указать этот параметр, если пакет драйверов не может быть однозначно идентифицируется по имени. Чтобы найти этот идентификатор для пакета, щелкните группу драйверов, в который входит пакет (или **все пакеты** узла), щелкните правой кнопкой мыши пакет и нажмите кнопку **свойства**. Идентификатор пакета указан на **Общие** вкладки. Например: {DD098D20-1850-4FC8-8E35-EA24A1BEFF5E}.|
|[/ Name:\<новое имя >]|Указывает новое имя для пакета драйверов.|
|[/ Включен: {Да | Нет}|Включает или отключает пакета.|

## <a name="BKMK_examples"></a>Примеры

Чтобы изменить параметры пакета, введите одно из следующих:
```
WDSUTIL /Set-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318} /Name:MyDriverPackage
```
```
WDSUTIL /Set-DriverPackage /DriverPackage:MyDriverPackage /Name:NewName /Enabled:Yes
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)