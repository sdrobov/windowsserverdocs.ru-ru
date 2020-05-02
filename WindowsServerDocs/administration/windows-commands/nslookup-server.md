---
title: nslookup server
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 608267f8-f7b4-412a-8dcd-e08b5ffc2085
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c9a3f4c7bdbcf8122bb532fafe83b400400d8d6b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723687"
---
# <a name="nslookup-server"></a>nslookup server

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет сервер по умолчанию на указанный домен службы доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
server <DNSDomain>
```
### <a name="parameters"></a>Параметры

|    Параметр    |                          Описание                           |
|-----------------|----------------------------------------------------------------|
|   <DNSDomain>   | Обязательный. Указывает новый домен DNS для сервера по умолчанию. |
| {Help &#124;?} |     Отображает краткую сводку подкоманд **nslookup** .      |

## <a name="remarks"></a>Примечания
- Команда **сервера** использует текущий сервер по умолчанию для поиска сведений об указанном домене DNS. Это отличается от команды **лсервер** , которая использует первоначальный сервер.
  ## <a name="additional-references"></a>Дополнительные ссылки
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [nslookup лсервер](nslookup-lserver.md)
