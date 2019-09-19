---
title: nslookup server
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 608267f8-f7b4-412a-8dcd-e08b5ffc2085
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e24e55026d12a0d8afc5b6f1bef926ece9087bd0
ms.sourcegitcommit: 6423dfa9cecb3b06bdd563cae113c3e80a4ec330
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2019
ms.locfileid: "71105009"
---
# <a name="nslookup-server"></a>nslookup server

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет сервер по умолчанию на указанный домен службы доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
server <DNSDomain>
```
## <a name="parameters"></a>Параметры

|    Параметр    |                          Описание                           |
|-----------------|----------------------------------------------------------------|
|   <DNSDomain>   | Обязательный. Указывает новый домен DNS для сервера по умолчанию. |
| {Help &#124; ?} |     Отображает краткую сводку подкоманд **nslookup** .      |

## <a name="remarks"></a>Примечания
- Команда **сервера** использует текущий сервер по умолчанию для поиска сведений об указанном домене DNS. Это отличается от команды **лсервер** , которая использует первоначальный сервер.
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса командной строки](command-line-syntax-key.md)[nslookup лсервер](nslookup-lserver.md) 
  
