---
title: Набор подкоманд-Дриверграуп
description: Справочная статья по подкоманде Set-Дриверграуп, которая задает свойства существующей группы драйверов на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e4ba9b1c-8c52-4fd5-969b-f7905611b364
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bffd46298dce4313f9506129faf0684413c0d08a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85937196"
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
|[/Server: <Server name> ]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|
|[/Name: <New Group Name> ]|Указывает новое имя для группы драйверов.|
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
- Ключ синтаксиса [командной строки](command-line-syntax-key.md) 
 [Подкоманда: Set-дриверграупфилтер](subcommand-set-drivergroupfilter.md)
