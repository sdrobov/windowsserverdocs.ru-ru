---
title: битсадмин сетвалидатионстате
description: Раздел команд Windows для **битсадмин сетвалидатионстате** — задает состояние проверки содержимого заданного файла в задании.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 37d7fa3a8a91abf1e7b6ac5a51b6cebd78984a91
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380396"
---
# <a name="bitsadmin-setvalidationstate"></a>битсадмин сетвалидатионстате



Задает состояние проверки содержимого заданного файла в задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetValidationState <Job> <file index> <true|false> 
```

## <a name="parameters"></a>Параметры

| Параметр  |          Описание           |
|------------|--------------------------------|
|    Job     | Отображаемое имя задания или идентификатор GUID |
| Индекс файла |         Начинается с 0          |
|    True    |             False              |

## <a name="BKMK_examples"></a>Примеров

В следующем примере состояние проверки содержимого файла 2 устанавливается равным TRUE для задания с именем *myJob*.
```
C:\>bitsadmin /SetValidationState myJob 2 TRUE 
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)