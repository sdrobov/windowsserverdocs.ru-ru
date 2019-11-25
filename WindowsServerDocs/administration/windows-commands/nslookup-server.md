---
title: nslookup server
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 0ce609f62f2d87024e1d75b43869b3b867e946e2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373064"
---
# <a name="nslookup-server"></a>nslookup server

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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

## <a name="remarks"></a>Замечания
- Команда **сервера** использует текущий сервер по умолчанию для поиска сведений об указанном домене DNS. Это отличается от команды **лсервер** , которая использует первоначальный сервер.
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [nslookup лсервер](nslookup-lserver.md)
