---
title: nslookup set domain
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9d4d28e8-6e88-42cc-801f-94e9d8e051f4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f6ee52cd5ad35dcfc6da1cd3885f66124338d62f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723609"
---
# <a name="nslookup-set-domain"></a>nslookup set domain

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет доменное имя DNS по умолчанию на указанное имя.
## <a name="syntax"></a>Синтаксис
```
set domain=<DomainName>
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                           Описание                                           |
|-----------------|-------------------------------------------------------------------------------------------------|
|  <DomainName>   | Указывает новое имя для доменного имени DNS по умолчанию. Доменное имя по умолчанию — имя узла. |
| {Help &#124;?} |                      Отображает краткую сводку подкоманд **nslookup** .                      |

## <a name="remarks"></a>Примечания
- Доменное имя DNS по умолчанию добавляется к поисковому запросу в зависимости от состояния параметров **дефнаме** и **поиска** . Список поиска доменов DNS содержит родительские домены DNS по умолчанию, если в имени содержится по крайней мере два компонента. Например, если домен DNS по умолчанию — mfg.widgets.com, список поиска будет называться как mfg.widgets.com, так и widgets.com. Используйте команду **Set срчлист** , чтобы указать другой список, и команда **Set All** для вывода списка.
  ## <a name="additional-references"></a>Дополнительные ссылки
  - [Синтаксис](command-line-syntax-key.md)
  командной строки[nslookup set срчлист](nslookup-set-srchlist.md)
  [nslookup set ALL](nslookup-set-all.md)
