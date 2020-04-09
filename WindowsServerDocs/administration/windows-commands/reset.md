---
title: сброс
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: afbdab44-199c-4e11-884f-e96804965c21
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5c27ddd93d06670a30f797bd58dd396a9e7ce70a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835787"
---
# <a name="reset"></a>сброс



Сбрасывает файл DiskShadow. exe в состояние по умолчанию. **Reset** особенно полезен при разделении составных операций DiskShadow, таких как **Создание**, **Импорт**, **резервное копирование**или **Восстановление**.

## <a name="syntax"></a>Синтаксис

```
reset
```

## <a name="remarks"></a>Примечания

-   При использовании команды **Reset** состояние теряется из таких команд, как **Add**, **Set**, **Load**или **Writer**. **Сброс** также освобождает ивссбаккупкомпонент интерфейсы и теряет непостоянные теневые копии.

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)