---
title: bitsadmin getmaxdownloadtime
description: Раздел Windows команды для **bitsadmin getmaxdownloadtime** -Возвращает время ожидания загрузки в секундах.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdce64f6-7125-489d-be3c-4af1dfc8c46a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d067d6a0821d9af4784c02c6a332e8eddd2352c0
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434944"
---
# <a name="bitsadmin-getmaxdownloadtime"></a>bitsadmin getmaxdownloadtime

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Возвращает время ожидания загрузки в секундах.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetMaxDownloadtime <Job> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

-   N\/A

## <a name="BKMK_examples"></a>Примеры
В следующем примере возвращается максимальное время загрузки задания с именем *myDownloadJob* в секундах.

```
C:\>bitsadmin /GetMaxDownloadtime myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)


