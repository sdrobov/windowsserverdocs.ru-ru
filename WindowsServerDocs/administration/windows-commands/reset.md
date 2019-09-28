---
title: сброс
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbdab44-199c-4e11-884f-e96804965c21
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a8903c300d12a019f8fb4aef6d367131a195d034
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371459"
---
# <a name="reset"></a>сброс



Сбрасывает файл DiskShadow. exe в состояние по умолчанию. **Reset** особенно полезен при разделении составных операций DiskShadow, таких как **Создание**, **Импорт**, **резервное копирование**или **Восстановление**.

## <a name="syntax"></a>Синтаксис

```
reset
```

## <a name="remarks"></a>Примечания

-   При использовании команды **Reset** состояние теряется из таких команд, как **Add**, **Set**, **Load**или **Writer**. **Сброс** также освобождает ивссбаккупкомпонент интерфейсы и теряет непостоянные теневые копии.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)