---
title: bdehdcfg newdriveletter
description: Раздел Windows команды для bdehdcfg newdriveletter - назначает новую букву часть диска используется в качестве системного диска.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f1f200a0-6850-4f0d-9047-f9f982a590f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cd40942dfb724d46c0fa9a43c4646e1db09d2a76
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59887145"
---
# <a name="bdehdcfg-newdriveletter"></a>bdehdcfg: newdriveletter



Назначает новый букву диска в часть диска используется в качестве системного диска. Пример того, как эту команду можно использовать, см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge} -newdriveletter <DriveLetter>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Буква диска >|Определяет букву диска, которая будет назначена указанной целевой диск.|

## <a name="remarks"></a>Примечания

Рекомендуется рекомендуется не назначить букву диска на локальный диск.

## <a name="BKMK_Examples"></a>Примеры

В следующем примере показано диска по умолчанию назначается буква диска P.
```
bdehdcfg -target default -newdriveletter P:
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Bdehdcfg](bdehdcfg.md)