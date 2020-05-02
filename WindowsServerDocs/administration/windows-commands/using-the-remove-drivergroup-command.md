---
title: Remove-Дриверграуп
description: Справочный раздел по Remove-Дриверграуп, который удаляет группу драйверов с сервера.
ms.prod: windows-server
ms.topic: article
ms.assetid: 1fefe9df-9782-433c-8abe-3f1a35e50da2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 314c7a73c7aeb49bc6bb96de23ca5bf4387bd932
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720418"
---
# <a name="remove-drivergroup"></a>Remove-Дриверграуп

Удаляет группу драйверов с сервера.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Remove-DriverGroup /DriverGroup:<Group Name> [/Server:<Server name>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/Дриверграуп:\<имя группы>|Указывает имя удаляемой группы драйверов.|
|[/Server:\<имя сервера>]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|

## <a name="examples"></a>Примеры

Чтобы удалить группу драйверов, введите одну из следующих:
```
WDSUTIL /Remove-DriverGroup /DriverGroup:PrinterDrivers
```
```
WDSUTIL /Remove-DriverGroup /DriverGroup:PrinterDrivers /Server:MyWdsServer
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)