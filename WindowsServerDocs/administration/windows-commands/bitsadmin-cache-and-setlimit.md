---
title: кэш bitsadmin и setlimit
description: Раздел Windows команды для **bitsadmin кэша и setlimit** -задает предельный размер кэша.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46578835-d5ce-423b-be4d-62ddb9e1908d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7d0b72c5ec6c779fa4ce3fa038352836cd9456ac
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852595"
---
# <a name="bitsadmin-cache-and-setlimit"></a>кэш bitsadmin и setlimit



Задает максимальный размер кэша.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Cache /SetLimit Percent
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Процентов|Ограничение кэша, определенное в процентах от общий объем дискового пространства...|

## <a name="BKMK_examples"></a>Примеры

Следующий пример ограничивает размер кэша 50%.
```
C:\>bitsadmin /Cache /SetLimit 50 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)