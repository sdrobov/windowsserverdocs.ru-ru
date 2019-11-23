---
title: средство
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7cf98295-411d-4705-8573-f898ff45c140
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6c00f6067cd5f6cf741cddbd6d62c5bcbb1f37a9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71361861"
---
# <a name="writer"></a>средство



Проверяет, включено ли средство записи или компонента, или исключает модуль записи или компонент из процедуры резервного копирования или восстановления. Если используется без параметров, **модуль записи** отображает справку в командной строке.

## <a name="syntax"></a>Синтаксис

```
writer verify [<Writer> | <Component>]
writer exclude [<Writer> | <Component>]
```

## <a name="parameters"></a>Параметры

| Параметр  |                                                                                      Описание                                                                                      |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   проверить   | Проверяет, что указанный модуль записи или компонент включен в процедуру резервного копирования или восстановления. Процедура резервного копирования или восстановления завершится ошибкой, если модуль записи или компонент не включен. |
|  exclude   |                                                   Исключает указанный модуль записи или компонент из процедуры резервного копирования или восстановления.                                                    |
| [модуль записи\<> |                                                                                     <Component>]                                                                                      |

## <a name="BKMK_examples"></a>Примеров

Чтобы проверить модуль записи, указав его идентификатор GUID (для этого примера — 4dc3bdd4-ab48-4d07-adb0-3bee2926fd7f), введите:
```
writer verify {4dc3bdd4-ab48-4d07-adb0-3bee2926fd7f}
```
Чтобы исключить модуль записи с именем "модуль записи системы", введите:
```
writer exclude "System Writer"
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)