---
title: диск сведений
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: ff78a3f9e27cde35a7e19bdf1565c515a127261b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378585"
---
# <a name="detail-disk"></a>диск сведений



Отображает свойства выбранного диска и тома на этом диске.

## <a name="syntax"></a>Синтаксис

```
detail disk
```

## <a name="remarks"></a>Примечания

-   Для выполнения этой операции необходимо выбрать диск. Используйте команду **Выбор диска** , чтобы выбрать диск и переместить фокус на него.
-   Если выбранный диск является виртуальным жестким диском (VHD), то **подробный диск** сообщает тип шины диска как виртуальный.

## <a name="BKMK_examples"></a>Примеров

Чтобы просмотреть свойства выбранного диска и сведения о томах на диске, введите:
```
detail disk
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

