---
title: bitsadmin getvalidationstate
description: 'Раздел Windows команды для **bitsadmin getvalidationstate** -сообщает о состоянии проверки содержимого для заданного файла, в рамках задания. '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6ada3f1f-9967-4262-9d22-ed641e23f516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8abff3fc9fddb9cff1758739fdc540a9c945efe2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879165"
---
# <a name="bitsadmin-getvalidationstate"></a>bitsadmin getvalidationstate



Сообщает о состоянии проверки содержимого для заданного файла, в рамках задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetValidationState <Job> <file index> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Индекс файла|Начинается с 0|

## <a name="BKMK_examples"></a>Примеры

В следующем примере возвращается состояние проверки содержимого файла 2 в рамках задания с именем *myJob*.
```
C:\>bitsadmin /GetValidationState myJob 1
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)