---
title: Набор подкоманд-Дриверграуп
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4ba9b1c-8c52-4fd5-969b-f7905611b364
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 751985cffea32b5129909576f0631cce83adc9a2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370843"
---
# <a name="subcommand-set-drivergroup"></a>Подкоманда: Set-Дриверграуп

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает свойства существующей группы драйверов на сервере.
## <a name="syntax"></a>Синтаксис
```
wdsutil /Set-DriverGroup /DriverGroup:<Group Name> [/Server:<Server Name>] [/Name:<New Group Name>] [/Enabled:{Yes | No}] [/Applicability:{Matched | All}]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/Дриверграуп:<Group Name>|Указывает имя группы драйверов.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|
|[/Name:<New Group Name>]|Указывает новое имя для группы драйверов.|
|[/Enabled: {Да &#124; }|Включает или отключает группу драйверов.|
|[/Аппликабилити: {сопоставлено &#124; всех}]|Указывает, какие пакеты следует установить при соблюдении условий фильтра. **Сопоставление** означает установку только пакетов драйверов, соответствующих оборудованию клиента. **Все** означает установку всех пакетов на клиентах независимо от их оборудования.|
## <a name="BKMK_examples"></a>Примеров
Чтобы задать свойства для группы драйверов, введите один из следующих параметров.
```
wdsutil /Set-DriverGroup /DriverGroup:printerdrivers /Enabled:Yes
```
```
wdsutil /Set-DriverGroup /DriverGroup:printerdrivers /Name:colorprinterdrivers /Applicability:All
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[подкоманды: Set-дриверграупфилтер](subcommand-set-drivergroupfilter.md)
