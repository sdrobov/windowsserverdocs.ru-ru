---
title: nslookup lserver
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 2f2f787915f2b941d6c098d44de1bb0e04dbd491
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436913"
---
# <a name="nslookup-lserver"></a>nslookup lserver

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменение сервера по умолчанию к указанному домену доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
lserver <DNSDomain> 
```
## <a name="parameters"></a>Параметры

|    Параметр    |                      Описание                      |
|-----------------|-------------------------------------------------------|
|   <DNSDomain>   | Указывает новый домен DNS для сервера по умолчанию.  |
| {help &#124; ?} | Отображает краткое описание **nslookup** подкоманды. |

## <a name="remarks"></a>Примечания
- **Lserver** команда использует исходным сервером для поиска сведений о домене DNS. Это отличается от **server** команду, которая использует текущий сервер.
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса команд](command-line-syntax-key.md)
  [nslookup server](nslookup-server.md)
