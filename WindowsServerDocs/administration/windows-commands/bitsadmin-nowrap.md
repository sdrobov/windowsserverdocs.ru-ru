---
title: bitsadmin nowrap
description: Раздел команд Windows для **битсадминing** — усекает любую строку выходного текста, выходящего за пределы крайнего правого края окна командной строки.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 85a47b90-783a-41e4-96f2-81f26ae8ca93
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3806ec51161eeae498e3c9b367b2aacf0bd32c99
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381050"
---
# <a name="bitsadmin-nowrap"></a>bitsadmin nowrap

Усекает любую строку выходного текста, выходящего за пределы крайнего правого края окна командной строки.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /NoWrap
```

## <a name="remarks"></a>Примечания

По умолчанию все параметры, кроме коммутатора **монитора** , заключают выходные данные в оболочку. Укажите параметр "не **переносить** " перед другими параметрами.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается состояние для задания с именем *мидовнлоаджоб* и не выполняется заключение в оболочку выходных данных.
```
C:\>bitsadmin /NoWrap /GetState myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)