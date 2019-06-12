---
title: bitsadmin getfilestotal
description: Раздел Windows команды для **bitsadmin getfilestotal** -извлекает число файлов в указанное задание.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5de113e-f29c-4cd3-9392-0e300018d516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b5f6d32b3410b182c510cf40b9def5370efafdc4
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66435123"
---
# <a name="bitsadmin-getfilestotal"></a>bitsadmin getfilestotal



Возвращает число файлов в указанное задание.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetFilesTotal <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается число файлов, которые включены в задание с именем *myDownloadJob*.
```
C:\>bitsadmin /GetFilesTotal myDownloadJob
```

# #

[Синтаксис командной строки Key](command-line-syntax-key.md) см. также