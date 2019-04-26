---
title: модуль записи
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 87b10952c6a851b5536a1589b994b265e8699f59
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59826405"
---
# <a name="writer"></a>модуль записи



Проверяет, модуль записи или компонент включается или исключает записи или компонент из процедуры резервного копирования или восстановления. При использовании без параметров, **записи** отображает справку в командной строке.

## <a name="syntax"></a>Синтаксис

```
writer verify [<Writer> | <Component>]
writer exclude [<Writer> | <Component>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|проверить|Проверяет, что в указанный модуль записи или компонент будут включены в процедуру резервного копирования или восстановления. Процедуры резервного копирования или восстановления завершится ошибкой, если модуль записи или компонент не включен.|
|exclude|Исключает указанный модуль записи или компонент из процедуры резервного копирования или восстановления.|
|[\<Записи > | <Component>]|Задает модуль записи или компонент, чтобы проверить или исключить. Указанные модули записи модулем записи GUID или имя модуля записи, например «модуль записи системы.»|

## <a name="BKMK_examples"></a>Примеры

Чтобы проверить модуль записи, указав его идентификатор GUID (например, 4dc3bdd4-ab48-4d07-adb0-3bee2926fd7f), введите следующую команду:
```
writer verify {4dc3bdd4-ab48-4d07-adb0-3bee2926fd7f}
```
Чтобы исключить записи с именем «модуль записи системы? Тип:
```
writer exclude "System Writer"
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)