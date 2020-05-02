---
title: сброс
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: afbdab44-199c-4e11-884f-e96804965c21
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0701324ad1ee94cc645c7519d81fef7357b6a34a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722346"
---
# <a name="reset"></a>сброс



Сбрасывает файл DiskShadow. exe в состояние по умолчанию. **Reset** особенно полезен при разделении составных операций DiskShadow, таких как **Создание**, **Импорт**, **резервное копирование**или **Восстановление**.

## <a name="syntax"></a>Синтаксис

```
reset
```

## <a name="remarks"></a>Примечания

-   При использовании команды **Reset** состояние теряется из таких команд, как **Add**, **Set**, **Load**или **Writer**. **Сброс** также освобождает ивссбаккупкомпонент интерфейсы и теряет непостоянные теневые копии.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)