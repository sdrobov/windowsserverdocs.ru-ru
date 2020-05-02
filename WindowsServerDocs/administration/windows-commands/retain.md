---
title: удержание
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: eeab0aef-2ba5-441a-a10d-bbef6f0d7e3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7391c0b60d07cc2eb5a6230b283ac180cc028508
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722341"
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

## <a name="additional-references"></a>Дополнительные ссылки

