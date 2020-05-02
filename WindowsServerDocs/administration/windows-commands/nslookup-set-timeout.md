---
title: nslookup set timeout
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 07afdaf4-ffec-496f-a188-4e91cf1a28f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 68e9630b9690c9b6c9d4c316f8b328897289362c
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723543"
---
# <a name="nslookup-set-timeout"></a>nslookup set timeout

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет начальное число секунд ожидания ответа на запрос поиска.
## <a name="syntax"></a>Синтаксис
```
set timeout=<Number>
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                           Описание                                            |
|-----------------|--------------------------------------------------------------------------------------------------|
|    <Number>     | Указывает количество секунд ожидания ответа. Значение по умолчанию (в секундах) ожидания равно 5. |
| {Help &#124;?} |                      Отображает краткую сводку подкоманд **nslookup** .                       |

## <a name="remarks"></a>Примечания
- Если ответ на запрос не получен в течение указанного периода времени, время ожидания удваивается и запрос отправляется снова. Для управления числом повторных попыток можно использовать команду **set retry** .
  ## <a name="examples"></a>Примеры
  Установка времени ожидания получения ответа в течение 2 секунд:
  ```
  set timeout=2
  ```
  ## <a name="additional-references"></a>Дополнительные ссылки
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [nslookup set retry](nslookup-set-retry.md)
