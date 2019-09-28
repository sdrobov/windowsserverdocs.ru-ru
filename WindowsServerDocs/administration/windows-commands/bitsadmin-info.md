---
title: bitsadmin info
description: Раздел команд Windows для **отображает сводную информацию об указанном задании.** -битсадмин сведения
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5c306677-0d64-41c0-8276-5bba7750cecb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3b6710d73860315fcd13670669871cd310ffb41c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381078"
---
# <a name="bitsadmin-info"></a>bitsadmin info



Отображает сводную информацию об указанном задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Info <Job> [/verbose]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Используйте параметр/Verbose для предоставления подробных сведений о задании.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекаются сведения о задании с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /Info myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)