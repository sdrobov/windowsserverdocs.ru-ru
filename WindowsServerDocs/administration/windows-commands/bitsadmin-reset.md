---
title: bitsadmin reset
description: Раздел команд Windows для **битсадмин Reset** . отменяет все задания в очереди на перемещение, принадлежащие текущему пользователю.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e4f9d1d-072c-493f-8d7a-f6d713c3ef29
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: adc6b07a7b5d1414c733fe6a3ac05eba7cb3029e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380811"
---
# <a name="bitsadmin-reset"></a>bitsadmin reset

Отменяет все задания в очереди на перемещение, которыми владеет текущий пользователь.

**Битсадмин 1,5 и более ранних версий**: Если у вас есть права администратора, **сбросьте** cancels все задания в очереди. Параметр/Аллусерс не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Reset [/AllUsers]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|AllUsers|Необязательно — отменяет все задания в очереди.|

## <a name="remarks"></a>Примечания

Для использования параметра **ALLUSERS** необходимо иметь права администратора.

> [!NOTE]
> Администраторы не могут сбрасывать задания, созданные локальной системой. Используйте Планировщик заданий, чтобы запланировать эту команду как задачу с помощью учетных данных локальной системы.

## <a name="BKMK_examples"></a>Примеров

В следующем примере отменяются все задания в очереди на перемещение для текущего пользователя.
```
C:\>bitsadmin /Reset
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)