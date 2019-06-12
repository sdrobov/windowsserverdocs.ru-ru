---
title: nslookup set srchlist
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8486266d-22ac-4ce5-aad6-1cd0c08110a2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 39b28e7d43df2427caae46d323cd30f03b6b484c
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436572"
---
# <a name="nslookup-set-srchlist"></a>nslookup set srchlist

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет значение по умолчанию доменных имен (DNS) и имя списке доменов.

## <a name="syntax"></a>Синтаксис
```
Set srchlist=<DomainName>[/...]
```
## <a name="parameters"></a>Параметры

|    Параметр    |                                                                                        Описание                                                                                        |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <DomainName>   | Указывает новые имена для списка домена и поиск DNS по умолчанию. Имя домена по умолчанию основан на имени узла. Можно указать до шести имен, разделенных косой чертой (/). |
| {help &#124; ?} |                                                                   Отображает краткое описание **nslookup** подкоманды.                                                                   |

## <a name="remarks"></a>Примечания
- **Set srchlist используется**переопределяет значение по умолчанию список DNS-домен и имя **домена набора** команды. Используйте **установить все** команду, чтобы отобразить в списке.
  ## <a name="BKMK_examples"></a>Примеры
  В следующем примере задается DNS-домена mfg.widgets.com и список поиска из трех имен:
  ```
  set srchlist=mfg.widgets.com/mrp2.widgets.com/widgets.com
  ```
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса команд](command-line-syntax-key.md)
  [nslookup задайте домен](nslookup-set-domain.md)
  [nslookup задать все](nslookup-set-all.md)
