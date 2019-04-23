---
title: break
description: 'Раздел Windows команды для **break_1** -наборов или очищает расширенных CTRL + C проверки системах MS-DOS. При использовании без параметров, **break** отображается текущее значение параметра. '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c89b7357-d69e-4141-826e-73c9ba0fc630
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d08eaa5194c8895aeb42ac58dfb68d2fc44e70bd
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59869055"
---
# <a name="break"></a>break



Задает или удаляет значение расширенной проверки системах MS-DOS CTRL + C. При использовании без параметров, **break** отображается текущее значение параметра.

> [!NOTE]
> Эта команда больше не используется. Она включена только для обеспечения совместимости с существующими файлами MS-DOS и ее применение не влияет на результат, поскольку необходимые действия выполняются автоматически.

## <a name="syntax"></a>Синтаксис

```
break=[on|off]
```

## <a name="remarks"></a>Примечания

Если включен и работает на платформе Windows, расширения команд вставки **break** команды в пакетном файле вводит жестко точки останова, если отлаживается отладчиком.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)