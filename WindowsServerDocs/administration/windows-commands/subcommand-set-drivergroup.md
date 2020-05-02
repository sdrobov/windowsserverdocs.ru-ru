---
title: Набор подкоманд-Дриверграуп
description: Справочный раздел по подкоманде Set-Дриверграуп, который задает свойства существующей группы драйверов на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e4ba9b1c-8c52-4fd5-969b-f7905611b364
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c70db688e17d185813298cea4fcee3b664f53d64
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721744"
---
# <a name="subcommand-set-drivergroup"></a>Подкоманда: Set-Дриверграуп

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает свойства существующей группы драйверов на сервере.

## <a name="syntax"></a>Синтаксис
```
wdsutil /Set-DriverGroup /DriverGroup:<Group Name> [/Server:<Server Name>] [/Name:<New Group Name>] [/Enabled:{Yes | No}] [/Applicability:{Matched | All}]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/Дриверграуп:<Group Name>|Указывает имя группы драйверов.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|
|[/Name:<New Group Name>]|Указывает новое имя для группы драйверов.|
|[/Enabled: {Yes &#124; No}|Включает или отключает группу драйверов.|
|[/Аппликабилити: {совпало &#124; ALL}]|Указывает, какие пакеты следует установить при соблюдении условий фильтра. **Сопоставление** означает установку только пакетов драйверов, соответствующих оборудованию клиента. **Все** означает установку всех пакетов на клиентах независимо от их оборудования.|
## <a name="examples"></a>Примеры
Чтобы задать свойства для группы драйверов, введите один из следующих параметров.
```
wdsutil /Set-DriverGroup /DriverGroup:printerdrivers /Enabled:Yes
```
```
wdsutil /Set-DriverGroup /DriverGroup:printerdrivers /Name:colorprinterdrivers /Applicability:All
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Command-Line Syntax Key](command-line-syntax-key.md)
Подкоманда для синтаксиса командной строки[: Set-дриверграупфилтер](subcommand-set-drivergroupfilter.md)
