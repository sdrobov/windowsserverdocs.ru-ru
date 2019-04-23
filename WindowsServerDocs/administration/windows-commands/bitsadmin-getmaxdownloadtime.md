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
ms.openlocfilehash: 868f7ac58a69c067681bf0597524fbaa5a25984f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842425"
---
#<a name="bitsadmin-getmaxdownloadtime"></a>bitsadmin getmaxdownloadtime

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
[Ключ синтаксиса командной строки](command-line-syntax-key.md)


