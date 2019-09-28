---
title: bitsadmin monitor
description: Раздел команд Windows для **монитора битсадмин** . отслеживает задания в очереди на перемещение, которой владеет текущий пользователь.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: fe4963349c7e17fc77500b5adfceafc48a20ac5f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381218"
---
# <a name="bitsadmin-monitor"></a>bitsadmin monitor



Отслеживает задания в очереди на перемещение, которыми владеет текущий пользователь.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Monitor [/allusers] [/refresh <Seconds>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|ALLUSERS|(Необязательно) — отслеживает задания для всех пользователей.|
|Обновить|(Необязательно) обновляет данные через интервал, заданный в *секундах*. Интервал обновления по умолчанию составляет 5 секунд.|

## <a name="remarks"></a>Примечания

Для использования параметра **ALLUSERS** необходимо иметь права администратора.

Нажмите клавиши CTRL + C, чтобы прервать обновление.

## <a name="BKMK_examples"></a>Примеров

В следующем примере производится мониторинг очереди на перемещение заданий, принадлежащих текущему пользователю, и обновление данных каждые 60 секунд.
```
C:\>bitsadmin /Monitor /refesh 60
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)