---
title: nslookup set retry
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 615fdfa2-fa29-47a8-8c9e-a6c5b45b3b71
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1baeeaefedc211434f46bd0cfad713f093a873bf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723586"
---
# <a name="nslookup-set-retry"></a>nslookup set retry

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает число повторных попыток.
## <a name="syntax"></a>Синтаксис
```
set retry=<Number>
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                      Описание                                       |
|-----------------|----------------------------------------------------------------------------------------|
|    <Number>     | Указывает новое значение для числа повторных попыток. По умолчанию число повторных попыток равно 4. |
| {Help &#124;?} |                 Отображает краткую сводку подкоманд **nslookup** .                  |

## <a name="remarks"></a>Примечания
- Если ответ на запрос не получен в течение определенного промежутка времени, время ожидания удваивается и запрос отсылается повторно. Значение параметра Retry определяет количество повторных попыток отправки запроса перед предоставлением. Вы можете изменить интервал ожидания с помощью подкоманды **Set timeout** .
  ## <a name="additional-references"></a>Дополнительные ссылки
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [nslookup set timeout](nslookup-set-timeout.md)
