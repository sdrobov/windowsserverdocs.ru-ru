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
ms.openlocfilehash: a832e8f3d21681f67a4486df33c387e5a8456718
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434869"
---
# <a name="bitsadmin-setvalidationstate"></a>bitsadmin setvalidationstate



Задает состояние проверки содержимого для заданного файла, в рамках задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetValidationState <Job> <file index> <true|false> 
```

## <a name="parameters"></a>Параметры

| Параметр  |          Описание           |
|------------|--------------------------------|
|    Job     | Отображаемое имя или идентификатор GUID задания |
| Индекс файла |         Начинается с 0          |
|    True    |             False              |

## <a name="BKMK_examples"></a>Примеры

В следующем примере задается состояние проверки содержимого файла 2 значение true для задания с именем *myJob*.
```
C:\>bitsadmin /SetValidationState myJob 2 TRUE 
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)