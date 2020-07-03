---
title: retain
description: Справочная статья для * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: eeab0aef-2ba5-441a-a10d-bbef6f0d7e3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 958ee0de7bd69c9391407ec6f4a832e1262746a2
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933071"
---
# <a name="retain"></a>retain



Подготавливает существующий динамический простой том для использования в качестве загрузочного или системного тома.

## <a name="syntax"></a>Синтаксис

```
retain
```

## <a name="remarks"></a>Примечания

-   На динамическом диске с основной загрузочной записью эта команда создает запись раздела в основной загрузочной записи.
-   На динамическом диске с таблицей разделов GPT эта команда создает запись секции в таблице разделов GUID.

## <a name="additional-references"></a>Дополнительные ссылки

