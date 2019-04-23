---
title: bitsadmin reset
description: Раздел Windows команды для **Сброс bitsadmin** — отменяет все задания в очереди передачи, которому принадлежит текущий пользователь.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: b7c29aac55393cd87145583814b3ffa8f0a2c3b3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59874255"
---
# <a name="bitsadmin-reset"></a>bitsadmin reset

Отменяет все задания в очереди передачи, которому принадлежит текущий пользователь.

**BITSAdmin 1.5 и более ранних**: Если у вас есть права администратора, **Сброс** отменяет все задания в очереди. Параметр /AllUsers не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Reset [/AllUsers]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|AllUsers|Необязательно — отменяет все задания в очереди.|

## <a name="remarks"></a>Примечания

Пользователь должен обладать правами администратора для использования **AllUsers** параметра.

> [!NOTE]
> Администраторы не могут сбрасывать заданиями, созданными Local System. Используйте планировщик задач, чтобы запланировать эту команду как задачу, используя учетные данные локальной системы.

## <a name="BKMK_examples"></a>Примеры

Следующий пример отменяет все задания в очереди передачи для текущего пользователя.
```
C:\>bitsadmin /Reset
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)