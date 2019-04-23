---
title: bitsadmin list
description: Раздел Windows команды для **bitsadmin списка** -перечислены задания передачи, принадлежащих текущему пользователю.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1416965e-e0e6-49cf-b1d4-b286d3cf8716
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f0b88001b9c4ae01b57006ffeef66dec0348ca77
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873865"
---
# <a name="bitsadmin-list"></a>bitsadmin list



Список заданий передачи, принадлежащих текущему пользователю.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /List [/allusers][/verbose]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/ Allusers|Необязательно — перечисляет задания для всех пользователей|
|/ Verbose|Необязательно — содержит подробные сведения для каждого задания.|

## <a name="remarks"></a>Примечания

Пользователь должен обладать правами администратора для использования параметра /allusers

## <a name="BKMK_examples"></a>Примеры

Следующий пример извлекает сведения о заданиях, принадлежащих текущему пользователю.
```
C:\>bitsadmin /List 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)