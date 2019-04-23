---
title: Подкоманды DriverGroup набора
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 6e645e16a3d78dd91bad98fedbb04896025b0eaf
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852705"
---
# <a name="subcommand-set-drivergroup"></a>Подкоманда: set-DriverGroup

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает свойства существующей группы драйверов на сервере.
## <a name="syntax"></a>Синтаксис
```
wdsutil /Set-DriverGroup /DriverGroup:<Group Name> [/Server:<Server Name>] [/Name:<New Group Name>] [/Enabled:{Yes | No}] [/Applicability:{Matched | All}]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ DriverGroup:<Group Name>|Задает имя группы драйверов.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.|
|[/ Name:<New Group Name>]|Указывает новое имя для группы драйверов.|
|[/ Включен: {Да &#124; нет}|Включает или отключает группу драйверов.|
|[/ Применимости: {соответствует &#124; все}]|Указывает, какие пакеты для установки при удовлетворении условий фильтра. **Соответствует** означает, что установка только пакетов драйверов, которые соответствуют оборудованию клиента s. **Все** означает, что установка всех пакетов на клиентах независимо от их оборудования.|
## <a name="BKMK_examples"></a>Примеры
Чтобы задать свойства для группы драйверов, введите одно из следующих:
```
wdsutil /Set-DriverGroup /DriverGroup:printerdrivers /Enabled:Yes
```
```
wdsutil /Set-DriverGroup /DriverGroup:printerdrivers /Name:colorprinterdrivers /Applicability:All
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[подкоманда: set-DriverGroupFilter](subcommand-set-drivergroupfilter.md)
