---
title: С помощью команды get-DriverGroup
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7cfe10c3-a63f-48e7-bef9-f6b474b4ddbe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7f82969e03b3474cf39afd2ae5c3ef2f9d4f8b5f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59847155"
---
# <a name="using-the-get-drivergroup-command"></a>С помощью команды get-DriverGroup

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о групп драйверов на сервере.
## <a name="syntax"></a>Синтаксис
```
wdsutil /Get-DriverGroup /DriverGroup:<Group Name> [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ DriverGroup:<Group Name>|Задает имя группы драйверов.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя.  Если имя сервера не указан, используется локальный сервер.|
|[/ Show: {PackageMetaData &#124; фильтры &#124; все}]|Отображает метаданные для всех пакетов драйверов в указанной группе. **PackageMetaData** отображаются сведения обо всех фильтрах, для группы драйверов. **Фильтры** отображает метаданные для всех пакетов драйверов и фильтры для группы.|
## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть сведения о файле драйвера, введите следующую команду:
```
wdsutil /Get-DriverGroup /DriverGroup:printerdrivers /Show:PackageMetaData
```
```
wdsutil /Get-DriverGroup /DriverGroup:printerdrivers /Server:MyWdsServer /Show:Filters
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды get-AllDriverGroups](using-the-get-alldrivergroups-command.md)
