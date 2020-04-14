---
title: Copy-Дриверграуп
description: Раздел команд Windows для Copy-Дриверграуп, который дублирует существующую группу драйверов на сервере, включая фильтры, пакеты драйверов и состояние включения или отключения.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0aaf6fa5-8b5b-4a1e-ae9b-8b5c6d89f571
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 277903150a25555b03b51c980436250656c597b1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831737"
---
# <a name="copy-drivergroup"></a>Copy-Дриверграуп

Дублирует существующую группу драйверов на сервере, включая фильтры, пакеты драйверов, состояние включения или отключения.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Copy-DriverGroup [/Server:<Server name>] /DriverGroup:<Source Group Name> /GroupName:<New Group Name>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[/Server:\<имя сервера >]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|
|/Дриверграуп:\<имя исходной группы >|Указывает имя исходной группы драйверов.|
|/Граупнаме:\<имя новой группы >|Указывает имя новой группы драйверов.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы скопировать группу драйверов, введите одну из следующих:
```
WDSUTIL /Copy-DriverGroup /Server:MyWdsServer /DriverGroup:PrinterDrivers /GroupName:X86PrinterDrivers
```
```
WDSUTIL /Copy-DriverGroup /DriverGroup:PrinterDrivers /GroupName:ColorPrinterDrivers
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)