---
title: удержание
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eeab0aef-2ba5-441a-a10d-bbef6f0d7e3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3b076e12c833645833f53a06476e62bbf44f2690
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384490"
---
# <a name="retain"></a>удержание



Подготавливает существующий динамический простой том для использования в качестве загрузочного или системного тома.

## <a name="syntax"></a>Синтаксис

```
retain
```

## <a name="remarks"></a>Примечания

-   На динамическом диске с основной загрузочной записью эта команда создает запись раздела в основной загрузочной записи.
-   На динамическом диске с таблицей разделов GPT эта команда создает запись секции в таблице разделов GUID.

#### <a name="additional-references"></a>Дополнительная справка

