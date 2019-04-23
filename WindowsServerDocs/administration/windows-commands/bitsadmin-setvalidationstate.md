---
title: bitsadmin setvalidationstate
description: Раздел Windows команды для **bitsadmin setvalidationstate** -задает состояние проверки содержимого для заданного файла, в рамках задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8fc8e8c-171c-4681-8057-6986b018e576
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 647389aaac06d1eb109052548c1b24f7579bde2f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59851245"
---
# <a name="bitsadmin-setvalidationstate"></a>bitsadmin setvalidationstate



Задает состояние проверки содержимого для заданного файла, в рамках задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetValidationState <Job> <file index> <true|false> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Индекс файла|Начинается с 0|
|True|False|Равным TRUE, если содержимое файла допустимо; в противном случае — значение FALSE|

## <a name="BKMK_examples"></a>Примеры

В следующем примере задается состояние проверки содержимого файла 2 значение true для задания с именем *myJob*.
```
C:\>bitsadmin /SetValidationState myJob 2 TRUE 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)