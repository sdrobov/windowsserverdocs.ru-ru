---
title: nslookup set srchlist
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8486266d-22ac-4ce5-aad6-1cd0c08110a2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8936daa3505b02295ae2f09c2910dead8d4c0ff8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723556"
---
# <a name="nslookup-set-srchlist"></a>nslookup set srchlist

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет доменное имя службы доменных имен (DNS) по умолчанию и список поиска.

## <a name="syntax"></a>Синтаксис
```
Set srchlist=<DomainName>[/...]
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                                                                        Описание                                                                                        |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <DomainName>   | Указывает новые имена для домена DNS по умолчанию и списка поиска. Значение доменного имени по умолчанию основано на имени узла. Можно указать не более шести имен, разделенных косыми чертами (/). |
| {Help &#124;?} |                                                                   Отображает краткую сводку подкоманд **nslookup** .                                                                   |

## <a name="remarks"></a>Примечания
- Команда **Set срчлист**переопределяет доменное имя DNS по умолчанию и список поиска для команды **set domain** . Чтобы отобразить список, используйте команду **Set All** .
  ## <a name="examples"></a>Примеры
  Чтобы задать для домена DNS значение mfg.widgets.com, а в списке поиска — три имени:
  ```
  set srchlist=mfg.widgets.com/mrp2.widgets.com/widgets.com
  ```
  ## <a name="additional-references"></a>Дополнительные ссылки
  - [Синтаксис](command-line-syntax-key.md)
  командной строки[nslookup set домен](nslookup-set-domain.md)
  [nslookup set ALL](nslookup-set-all.md)
