---
title: nslookup set timeout
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07afdaf4-ffec-496f-a188-4e91cf1a28f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 32fcfcaeccb6599e9aaca21f9c085bb00857479c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372764"
---
# <a name="nslookup-set-timeout"></a>nslookup set timeout

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет начальное число секунд ожидания ответа на запрос поиска.
## <a name="syntax"></a>Синтаксис
```
set timeout=<Number>
```
## <a name="parameters"></a>Параметры

|    Параметр    |                                           Описание                                            |
|-----------------|--------------------------------------------------------------------------------------------------|
|    <Number>     | Указывает количество секунд ожидания ответа. Значение по умолчанию (в секундах) ожидания равно 5. |
| {Help &#124; ?} |                      Отображает краткую сводку подкоманд **nslookup** .                       |

## <a name="remarks"></a>Примечания
- Если ответ на запрос не получен в течение указанного периода времени, время ожидания удваивается и запрос отправляется снова. Для управления числом повторных попыток можно использовать команду **set retry** .
  ## <a name="BKMK_examples"></a>Примеров
  В следующем примере устанавливается время ожидания для получения ответа в течение 2 секунд:
  ```
  set timeout=2
  ```
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Синтаксис командной строки](command-line-syntax-key.md)
  [параметр nslookup set retry](nslookup-set-retry.md)
