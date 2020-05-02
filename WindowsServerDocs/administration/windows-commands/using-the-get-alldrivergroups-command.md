---
title: Get-Аллдриверграупс
description: Справочный раздел по Get-Аллдриверграупс, в котором отображаются сведения обо всех группах драйверов на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f245ba53-f150-41b1-8418-38dcf0410a05
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c4ac3e0c7b05c96383714c3a702cffd6aa8df18a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720892"
---
# <a name="get-alldrivergroups"></a>Get-Аллдриверграупс

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения обо всех группах драйверов на сервере.

## <a name="syntax"></a>Синтаксис
```
wdsutil /Get-AllDriverGroups [/Server:<Server name>] [/Show:{PackageMetaData | Filters | All}]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.|
|[/Show: {Паккажеметадата &#124; фильтры &#124; все}]|Отображает метаданные для всех пакетов драйверов в указанной группе. **Паккажеметадата** отображает сведения обо всех фильтрах для группы драйверов. **Фильтры** отображает метаданные для всех пакетов драйверов и фильтров для группы.|
## <a name="examples"></a>Примеры
Чтобы просмотреть сведения о файле драйвера, введите:
```
wdsutil /Get-AllDriverGroups /Server:MyWdsServer /Show:All
```
```
wdsutil /Get-AllDriverGroups [/Show:PackageMetaData]
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды Get-дриверграуп](using-the-get-drivergroup-command.md)
