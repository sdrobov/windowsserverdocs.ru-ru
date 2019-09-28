---
title: nslookup set retry
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 615fdfa2-fa29-47a8-8c9e-a6c5b45b3b71
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 306bcc4f5e7ac98767c3c2e274100cf917874a8e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372861"
---
# <a name="nslookup-set-retry"></a>nslookup set retry

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает число повторных попыток.
## <a name="syntax"></a>Синтаксис
```
set retry=<Number>
```
## <a name="parameters"></a>Параметры

|    Параметр    |                                      Описание                                       |
|-----------------|----------------------------------------------------------------------------------------|
|    <Number>     | Указывает новое значение для числа повторных попыток. По умолчанию число повторных попыток равно 4. |
| {Help &#124; ?} |                 Отображает краткую сводку подкоманд **nslookup** .                  |

## <a name="remarks"></a>Примечания
- Если ответ на запрос не получен в течение определенного промежутка времени, время ожидания удваивается и запрос отсылается повторно. Значение параметра Retry определяет количество повторных попыток отправки запроса перед предоставлением. Вы можете изменить интервал ожидания с помощью подкоманды **Set timeout** .
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Синтаксис командной строки](command-line-syntax-key.md)
  [параметр nslookup set timeout](nslookup-set-timeout.md)
