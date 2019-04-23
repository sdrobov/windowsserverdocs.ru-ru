---
title: Сохранить
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 4b437e9f0c8d671e4378311d450aa0ac7639219f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852175"
---
# <a name="retain"></a>Сохранить



Подготовка существующего динамического простого тома для использования в качестве загрузочного или системного тома.

## <a name="syntax"></a>Синтаксис

```
retain
```

## <a name="remarks"></a>Примечания

-   На динамическом диске основной загрузочной записью (MBR) эта команда создает запись раздела в главной загрузочной записи.
-   Идентификатор GUID секции таблицы (GPT) динамического диска эта команда создает запись раздела в таблице разделов.

#### <a name="additional-references"></a>Дополнительная справка

