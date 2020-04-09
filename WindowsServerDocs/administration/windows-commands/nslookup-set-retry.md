---
title: nslookup set retry
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 615fdfa2-fa29-47a8-8c9e-a6c5b45b3b71
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2b95c4c8af2d7960270fd43f7a766b313ddbc07a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838347"
---
# <a name="nslookup-set-retry"></a>nslookup set retry

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает число повторных попыток.
## <a name="syntax"></a>Синтаксис
```
set retry=<Number>
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                      Описание                                       |
|-----------------|----------------------------------------------------------------------------------------|
|    <Number>     | Указывает новое значение для числа повторных попыток. По умолчанию число повторных попыток равно 4. |
| {Help &#124; ?} |                 Отображает краткую сводку подкоманд **nslookup** .                  |

## <a name="remarks"></a>Примечания
- Если ответ на запрос не получен в течение определенного промежутка времени, время ожидания удваивается и запрос отсылается повторно. Значение параметра Retry определяет количество повторных попыток отправки запроса перед предоставлением. Вы можете изменить интервал ожидания с помощью подкоманды **Set timeout** .
  ## <a name="additional-references"></a>Дополнительные материалы
  - [Синтаксис командной строки](command-line-syntax-key.md)
  параметру [nslookup set timeout](nslookup-set-timeout.md)
