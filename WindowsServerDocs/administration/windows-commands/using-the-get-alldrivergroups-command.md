---
title: С помощью команды get-AllDriverGroups
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f245ba53-f150-41b1-8418-38dcf0410a05
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 236a2f798fb07ee6eafb9baf9314dbf46a984cdf
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59874005"
---
# <a name="using-the-get-alldrivergroups-command"></a>С помощью команды get-AllDriverGroups

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о всех групп драйверов на сервере.
## <a name="syntax"></a>Синтаксис
```
wdsutil /Get-AllDriverGroups [/Server:<Server name>] [/Show:{PackageMetaData | Filters | All}]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.|
|[/ Show: {PackageMetaData &#124; фильтры &#124; все}]|Отображает метаданные для всех пакетов драйверов в указанной группе. **PackageMetaData** отображаются сведения обо всех фильтрах, для группы драйверов. **Фильтры** отображает метаданные для всех пакетов драйверов и фильтры для группы.|
## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть сведения о файле драйвера, введите следующую команду:
```
wdsutil /Get-AllDriverGroups /Server:MyWdsServer /Show:All
```
```
wdsutil /Get-AllDriverGroups [/Show:PackageMetaData]
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды get-DriverGroup](using-the-get-drivergroup-command.md)
