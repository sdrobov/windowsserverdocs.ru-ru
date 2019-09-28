---
title: nslookup set srchlist
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: fb93a9f7cf969161536e88bec929b7e6ba0f0e5d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372768"
---
# <a name="nslookup-set-srchlist"></a>nslookup set srchlist

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет доменное имя службы доменных имен (DNS) по умолчанию и список поиска.

## <a name="syntax"></a>Синтаксис
```
Set srchlist=<DomainName>[/...]
```
## <a name="parameters"></a>Параметры

|    Параметр    |                                                                                        Описание                                                                                        |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <DomainName>   | Указывает новые имена для домена DNS по умолчанию и списка поиска. Значение доменного имени по умолчанию основано на имени узла. Можно указать не более шести имен, разделенных косыми чертами (/). |
| {Help &#124; ?} |                                                                   Отображает краткую сводку подкоманд **nslookup** .                                                                   |

## <a name="remarks"></a>Примечания
- Команда **Set срчлист**переопределяет доменное имя DNS по умолчанию и список поиска для команды **set domain** . Чтобы отобразить список, используйте команду **Set All** .
  ## <a name="BKMK_examples"></a>Примеров
  В следующем примере для домена DNS задается имя mfg.widgets.com, а в списке поиска — три.
  ```
  set srchlist=mfg.widgets.com/mrp2.widgets.com/widgets.com
  ```
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Синтаксис командной строки](command-line-syntax-key.md)
  [nslookup set domain](nslookup-set-domain.md)
  [nslookup set ALL](nslookup-set-all.md)
