---
title: сброс
description: Справочная статья для * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: afbdab44-199c-4e11-884f-e96804965c21
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8a412eff7bdf432608a999edb4531074ed5e8f26
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933091"
---
# <a name="reset"></a>сброс



Сбрасывает DiskShadow.exe в состояние по умолчанию. **Reset** особенно полезен при разделении составных операций DiskShadow, таких как **Создание**, **Импорт**, **резервное копирование**или **Восстановление**.

## <a name="syntax"></a>Синтаксис

```
reset
```

## <a name="remarks"></a>Примечания

-   При использовании команды **Reset** состояние теряется из таких команд, как **Add**, **Set**, **Load**или **Writer**. **Сброс** также освобождает ивссбаккупкомпонент интерфейсы и теряет непостоянные теневые копии.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)