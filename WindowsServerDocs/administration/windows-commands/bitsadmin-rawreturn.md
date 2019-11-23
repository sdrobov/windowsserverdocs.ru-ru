---
title: bitsadmin rawreturn
description: Раздел команд Windows для **битсадмин равретурн** . Возвращает данные, подходящие для синтаксического анализа.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bbe97130-26f6-4cdd-84f1-baf530ce38b7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 86d769de460538acda696194348980de5752d6d8
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380884"
---
# <a name="bitsadmin-rawreturn"></a>bitsadmin rawreturn

Возвращает данные, подходящие для синтаксического анализа.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /RawReturn
```

## <a name="remarks"></a>Замечания

Удаляет символы новой строки и форматирование из выходных данных.

Как правило, эта команда используется совместно с параметрами **CREATE** и **Get\\** * для получения только значения. Этот параметр необходимо указать перед другими коммутаторами.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекаются необработанные данные для состояния задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /RawReturn /GetState myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)