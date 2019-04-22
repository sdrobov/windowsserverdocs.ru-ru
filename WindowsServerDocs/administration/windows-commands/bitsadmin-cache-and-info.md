---
title: bitsadmin кэша и сведения
description: Раздел Windows команды для **bitsadmin кэша и сведения о** -дампов конкретной записи кэша.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 15975cbf-dba6-49ca-a725-d15ce1952de5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 61ff57b33e575921f2032d4e13a2d9b74accae60
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813325"
---
# <a name="bitsadmin-cache-and-info"></a>bitsadmin кэша и сведения



Создает дамп конкретной записи кэша.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Cache /Info RecordID [/Verbose] 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|RecordID|Идентификатор GUID, связанный с записью кэша.|

## <a name="BKMK_examples"></a>Примеры

Следующий пример выводит запись кэша с RecordID {6511FB02-E195-40A2-B595-E8E2F8F47702}.
```
C:\>bitsadmin /Cache /Info {6511FB02-E195-40A2-B595-E8E2F8F47702} 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)