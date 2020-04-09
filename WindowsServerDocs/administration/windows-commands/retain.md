---
title: удержание
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: eeab0aef-2ba5-441a-a10d-bbef6f0d7e3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 891192c0d6b1687cf6bffea0f57d1853e023b776
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835767"
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

## <a name="additional-references"></a>Дополнительные материалы

