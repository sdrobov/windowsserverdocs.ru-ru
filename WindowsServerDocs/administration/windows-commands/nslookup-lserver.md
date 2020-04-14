---
title: nslookup lserver
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aee5ea0b-bb17-4c14-bde7-2f7a91f2f22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9d0d8619101d2e7b1f7fb6d6ed99d801c7c264f1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838637"
---
# <a name="nslookup-lserver"></a>nslookup lserver

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет сервер по умолчанию на указанный домен службы доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
lserver <DNSDomain> 
```
### <a name="parameters"></a>Параметры

|    Параметр    |                      Описание                      |
|-----------------|-------------------------------------------------------|
|   <DNSDomain>   | Указывает новый домен DNS для сервера по умолчанию.  |
| {Help &#124; ?} | Отображает краткую сводку подкоманд **nslookup** . |

## <a name="remarks"></a>Примечания
- Команда **лсервер** использует исходный сервер для поиска сведений об указанном домене DNS. Это отличается от команды **Server** , которая использует текущий сервер по умолчанию.
  ## <a name="additional-references"></a>Дополнительные материалы
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [nslookup Server](nslookup-server.md)
