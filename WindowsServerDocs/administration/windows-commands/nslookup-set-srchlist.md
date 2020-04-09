---
title: nslookup set srchlist
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8486266d-22ac-4ce5-aad6-1cd0c08110a2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bbeb09501474ade670147a6021abd2bb25291d71
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838287"
---
# <a name="nslookup-set-srchlist"></a>nslookup set srchlist

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет доменное имя службы доменных имен (DNS) по умолчанию и список поиска.

## <a name="syntax"></a>Синтаксис
```
Set srchlist=<DomainName>[/...]
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                                                                        Описание                                                                                        |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <DomainName>   | Указывает новые имена для домена DNS по умолчанию и списка поиска. Значение доменного имени по умолчанию основано на имени узла. Можно указать не более шести имен, разделенных косыми чертами (/). |
| {Help &#124; ?} |                                                                   Отображает краткую сводку подкоманд **nslookup** .                                                                   |

## <a name="remarks"></a>Примечания
- Команда **Set срчлист**переопределяет доменное имя DNS по умолчанию и список поиска для команды **set domain** . Чтобы отобразить список, используйте команду **Set All** .
  ## <a name="examples"></a><a name=BKMK_examples></a>Примеров
  В следующем примере для домена DNS задается имя mfg.widgets.com, а в списке поиска — три.
  ```
  set srchlist=mfg.widgets.com/mrp2.widgets.com/widgets.com
  ```
  ## <a name="additional-references"></a>Дополнительные материалы
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [nslookup set domain](nslookup-set-domain.md)
  [nslookup set ALL](nslookup-set-all.md)
