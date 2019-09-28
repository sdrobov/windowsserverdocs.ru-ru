---
title: nslookup lserver
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aee5ea0b-bb17-4c14-bde7-2f7a91f2f22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 347ad6e380f8d8163c4954771c9e985271b2d549
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373080"
---
# <a name="nslookup-lserver"></a>nslookup lserver

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет сервер по умолчанию на указанный домен службы доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
lserver <DNSDomain> 
```
## <a name="parameters"></a>Параметры

|    Параметр    |                      Описание                      |
|-----------------|-------------------------------------------------------|
|   <DNSDomain>   | Указывает новый домен DNS для сервера по умолчанию.  |
| {Help &#124; ?} | Отображает краткую сводку подкоманд **nslookup** . |

## <a name="remarks"></a>Примечания
- Команда **лсервер** использует исходный сервер для поиска сведений об указанном домене DNS. Это отличается от команды **Server** , которая использует текущий сервер по умолчанию.
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса командной строки](command-line-syntax-key.md)для[сервера nslookup](nslookup-server.md) 
  
