---
title: nslookup set
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1fe5b36d-e93e-468b-abca-43b0204b32d1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2e416fb3bf8dafa72f0c46a018723aa75ae621de
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723518"
---
# <a name="nslookup-set"></a>nslookup set

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
| {Help &#124;?} |                                                                                               Отображает краткую сводку подкоманд **nslookup** .                                                                                               |

## <a name="remarks"></a>Примечания
Используйте **параметр Set All** , чтобы просмотреть список текущих параметров.
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[nslookup set ALL](nslookup-set-all.md)
