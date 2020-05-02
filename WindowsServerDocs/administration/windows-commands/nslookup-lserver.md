---
title: nslookup lserver
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aee5ea0b-bb17-4c14-bde7-2f7a91f2f22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b2054c0fd427b41e7d6076258b29ab78d0fb7892
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723676"
---
# <a name="nslookup-lserver"></a>nslookup lserver

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет сервер по умолчанию на указанный домен службы доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
lserver <DNSDomain> 
```
### <a name="parameters"></a>Параметры

|    Параметр    |                      Описание                      |
|-----------------|-------------------------------------------------------|
|   <DNSDomain>   | Указывает новый домен DNS для сервера по умолчанию.  |
| {Help &#124;?} | Отображает краткую сводку подкоманд **nslookup** . |

## <a name="remarks"></a>Примечания
- Команда **лсервер** использует исходный сервер для поиска сведений об указанном домене DNS. Это отличается от команды **Server** , которая использует текущий сервер по умолчанию.
  ## <a name="additional-references"></a>Дополнительные ссылки
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  для[сервера nslookup](nslookup-server.md)
