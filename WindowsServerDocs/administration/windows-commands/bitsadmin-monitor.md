---
title: bitsadmin monitor
description: Раздел Windows команды для **bitsadmin монитор** -отслеживает заданий в очереди передачи, которому принадлежит текущий пользователь.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c424d27-e011-49c2-b579-a2c235467c39
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2c4620d5c8e46cb8bfcb6b9c83261d57781abea5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814595"
---
# <a name="bitsadmin-monitor"></a>bitsadmin monitor



Отслеживание заданий в очереди передачи, которому принадлежит текущий пользователь.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Monitor [/allusers] [/refresh <Seconds>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|ALLUSERS|Необязательно — отслеживает заданий для всех пользователей.|
|Обновить|Необязательно — обновляет данные в интервале, заданном элементом *секунд*. Интервал обновления по умолчанию — пять секунд.|

## <a name="remarks"></a>Примечания

Пользователь должен обладать правами администратора для использования **Allusers** параметра.

Используйте сочетание клавиш CTRL + C для остановки обновления.

## <a name="BKMK_examples"></a>Примеры

В следующем примере отслеживает очередь передачи для задания, принадлежащие текущему пользователю и обновляет данные каждые 60 секунд.
```
C:\>bitsadmin /Monitor /refesh 60
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)