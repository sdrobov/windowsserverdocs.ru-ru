---
title: nslookup set
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1fe5b36d-e93e-468b-abca-43b0204b32d1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3883e6b032c5a4542711ad14a4e45b31fb605485
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838147"
---
# <a name="nslookup-set"></a>nslookup set

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет параметры конфигурации, влияющие на работу функций Lookup.
## <a name="syntax"></a>Синтаксис
```
set <KeyWord>[=<Value>]
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                                                                                                    Описание                                                                                                                    |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    <KeyWord>    | Определяет подкоманды, которые являются производными от подкоманды **Set** . Например, набор подкоманд **D2** имеет ключевое слово [**No**]**D2**. Список подкоманд, которые являются производными от подкоманды **Set** , см. в разделе Дополнительные ссылки. |
|     <Value>     |                                                                                      Задает значение параметра конфигурации nslookup для каждой подкоманды.                                                                                      |
| {Help &#124; ?} |                                                                                               Отображает краткую сводку подкоманд **nslookup** .                                                                                               |

## <a name="remarks"></a>Примечания
Используйте **параметр Set All** , чтобы просмотреть список текущих параметров.
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[nslookup set ALL](nslookup-set-all.md)
