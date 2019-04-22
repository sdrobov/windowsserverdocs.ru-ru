---
title: bitsadmin nowrap
description: Раздел Windows команды для **bitsadmin nowrap** -усекает любую строку вывода текста, выходящие за пределы правый край окна команд.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 4130f606a6b1874e1ea31952160de44d6e09c6b6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59822925"
---
# <a name="bitsadmin-nowrap"></a>bitsadmin nowrap

Усекает любую строку вывода текста, выходящие за пределы правый край окна команд.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /NoWrap
```

## <a name="remarks"></a>Примечания

По умолчанию всех коммутаторов, за исключением **монитор** переключения, поместите выходные данные. Укажите **NoWrap** переключения, прежде чем другими параметрами.

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается состояние задания с именем *myDownloadJob* и не переносит выходные данные
```
C:\>bitsadmin /NoWrap /GetState myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)