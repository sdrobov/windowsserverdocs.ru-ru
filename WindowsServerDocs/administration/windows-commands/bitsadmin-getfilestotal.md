---
title: bitsadmin getfilestotal
description: Раздел команд Windows для **битсадмин жетфилестотал** — извлекает количество файлов в указанном задании.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 27cf04e8745aeab5cd1f2ce379c8506be642fea2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381614"
---
# <a name="bitsadmin-getfilestotal"></a>bitsadmin getfilestotal



Извлекает количество файлов в указанном задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetFilesTotal <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается число файлов, включаемых в задание с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetFilesTotal myDownloadJob
```

# #

[Ключ синтаксиса командной строки](command-line-syntax-key.md) См. также