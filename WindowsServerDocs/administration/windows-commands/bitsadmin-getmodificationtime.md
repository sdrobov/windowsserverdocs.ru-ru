---
title: bitsadmin getmodificationtime
description: Раздел Windows команды для **bitsadmin getmodificationtime** -извлекает последнего изменения задания времени или данных успешно перенесены.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e543945e-92c4-491e-8c2d-344f8a3e342d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4257f0ae4868b2f18221ab99268384f778c4bbbe
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59837025"
---
# <a name="bitsadmin-getmodificationtime"></a>bitsadmin getmodificationtime



Получает время последнего изменения задания или данных успешно перенесены.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetModificationTime <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

Следующий пример извлекает время последнего изменения задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetModificationTime myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)