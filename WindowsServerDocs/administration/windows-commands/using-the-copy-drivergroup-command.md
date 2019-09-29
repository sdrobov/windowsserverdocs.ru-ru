---
title: Использование команды Copy-Дриверграуп
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0aaf6fa5-8b5b-4a1e-ae9b-8b5c6d89f571
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c08ce616c9b0e2bf79c7f13f922e27d7f7f7ca62
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363591"
---
# <a name="using-the-copy-drivergroup-command"></a>Использование команды Copy-Дриверграуп



Дублирует существующую группу драйверов на сервере, включая фильтры, пакеты драйверов, состояние включения или отключения.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Copy-DriverGroup [/Server:<Server name>] /DriverGroup:<Source Group Name> /GroupName:<New Group Name>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[/Server: \<Server имя >]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|
|/Дриверграуп: @no__t — имя группы 0Source >|Указывает имя исходной группы драйверов.|
|/Граупнаме: @no__t — имя группы 0New >|Указывает имя новой группы драйверов.|

## <a name="BKMK_examples"></a>Примеров

Чтобы скопировать группу драйверов, введите одну из следующих:
```
WDSUTIL /Copy-DriverGroup /Server:MyWdsServer /DriverGroup:PrinterDrivers /GroupName:X86PrinterDrivers
```
```
WDSUTIL /Copy-DriverGroup /DriverGroup:PrinterDrivers /GroupName:ColorPrinterDrivers
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)