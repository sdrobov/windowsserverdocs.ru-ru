---
title: nslookup set domain
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9d4d28e8-6e88-42cc-801f-94e9d8e051f4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fa433383e23fd19779960348e0af88e0a405ff83
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838467"
---
# <a name="nslookup-set-domain"></a>nslookup set domain

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет доменное имя DNS по умолчанию на указанное имя.
## <a name="syntax"></a>Синтаксис
```
set domain=<DomainName>
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                           Описание                                           |
|-----------------|-------------------------------------------------------------------------------------------------|
|  <DomainName>   | Указывает новое имя для доменного имени DNS по умолчанию. Доменное имя по умолчанию — имя узла. |
| {Help &#124; ?} |                      Отображает краткую сводку подкоманд **nslookup** .                      |

## <a name="remarks"></a>Примечания
- Доменное имя DNS по умолчанию добавляется к поисковому запросу в зависимости от состояния параметров **дефнаме** и **поиска** . Список поиска доменов DNS содержит родительские домены DNS по умолчанию, если в имени содержится по крайней мере два компонента. Например, если домен DNS по умолчанию — mfg.widgets.com, список поиска будет называться как mfg.widgets.com, так и widgets.com. Используйте команду **Set срчлист** , чтобы указать другой список, и команда **Set All** для вывода списка.
  ## <a name="additional-references"></a>Дополнительные материалы
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [nslookup set срчлист](nslookup-set-srchlist.md)
  [nslookup set ALL](nslookup-set-all.md)
