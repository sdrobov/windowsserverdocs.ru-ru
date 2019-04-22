---
title: сведения о диске
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b09cf40-8d93-452b-b449-5242e62a4102
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2c7a5063edf3cb2e190e8aec957e1b571c1f15bc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59819105"
---
# <a name="detail-disk"></a>сведения о диске



Отображает свойства выбранного диска и тома на этом диске.

## <a name="syntax"></a>Синтаксис

```
detail disk
```

## <a name="remarks"></a>Примечания

-   Для успешного выполнения этой операции необходимо выбрать диск. Используйте **выберите диск** команду, чтобы выбрать диск и перетянуть внимание к нему.
-   Если выбранный диск — это виртуальный жесткий диск (VHD), **диска подробно** сообщает тип дисковой шины, как Virtual.

## <a name="BKMK_examples"></a>Примеры

Чтобы просмотреть свойства выбранного диска и сведения о томах на диске, введите следующую команду:
```
detail disk
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

