---
title: кэш битсадмин и сведения
description: Раздел команд Windows для **кэша битсадмин и info** — создает дамп определенной записи кэша.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 11963ff5640ef30e597e5e802778aff121c0efb3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381968"
---
# <a name="bitsadmin-cache-and-info"></a>кэш битсадмин и сведения



Создает дамп определенной записи кэша.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Cache /Info RecordID [/Verbose] 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|RecordID|Идентификатор GUID, связанный с записью кэша.|

## <a name="BKMK_examples"></a>Примеров

В следующем примере запись кэша выводится с помощью RecordID для {6511FB02-E195-40A2-B595-E8E2F8F47702}.
```
C:\>bitsadmin /Cache /Info {6511FB02-E195-40A2-B595-E8E2F8F47702} 
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)