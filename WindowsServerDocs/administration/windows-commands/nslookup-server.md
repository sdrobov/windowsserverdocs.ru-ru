---
title: nslookup server
description: 'Раздел Windows команды для ***- '
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
ms.openlocfilehash: ba58e223d0aa35b4157b813b10bf1d274313a1c1
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436968"
---
# <a name="nslookup-server"></a>nslookup server

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменение сервера по умолчанию к указанному домену доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
server <DNSDomain>
```
## <a name="parameters"></a>Параметры

|    Параметр    |                          Описание                           |
|-----------------|----------------------------------------------------------------|
|   <DNSDomain>   | Обязательный. Указывает новый домен DNS для сервера по умолчанию. |
| {help &#124; ?} |     Отображает краткое описание **nslookup** подкоманды.      |

## <a name="remarks"></a>Примечания
- **Server** команда текущий сервер использует для поиска информации о домене DNS. Это отличается от **lserver** команду, которая использует исходным сервером.
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса команд](command-line-syntax-key.md)
  [nslookup lserver](nslookup-lserver.md)
