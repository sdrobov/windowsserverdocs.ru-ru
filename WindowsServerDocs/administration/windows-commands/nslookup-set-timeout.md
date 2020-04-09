---
title: nslookup set timeout
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 07afdaf4-ffec-496f-a188-4e91cf1a28f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8506511fc203f94d395851471f6a981ef0765928
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838277"
---
# <a name="nslookup-set-timeout"></a>nslookup set timeout

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет начальное число секунд ожидания ответа на запрос поиска.
## <a name="syntax"></a>Синтаксис
```
set timeout=<Number>
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                           Описание                                            |
|-----------------|--------------------------------------------------------------------------------------------------|
|    <Number>     | Указывает количество секунд ожидания ответа. Значение по умолчанию (в секундах) ожидания равно 5. |
| {Help &#124; ?} |                      Отображает краткую сводку подкоманд **nslookup** .                       |

## <a name="remarks"></a>Примечания
- Если ответ на запрос не получен в течение указанного периода времени, время ожидания удваивается и запрос отправляется снова. Для управления числом повторных попыток можно использовать команду **set retry** .
  ## <a name="examples"></a><a name=BKMK_examples></a>Примеров
  В следующем примере устанавливается время ожидания для получения ответа в течение 2 секунд:
  ```
  set timeout=2
  ```
  ## <a name="additional-references"></a>Дополнительные материалы
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [nslookup set retry](nslookup-set-retry.md)
