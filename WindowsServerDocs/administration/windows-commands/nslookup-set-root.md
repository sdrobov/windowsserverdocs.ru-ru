---
title: nslookup set root
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8ad5393c-d4fd-4594-8187-576b1dcde60a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d913669fd4fede06c9983756df1bbf626ca430ac
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723570"
---
# <a name="nslookup-set-root"></a>nslookup set root

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет имя корневого сервера, используемого для запросов.
## <a name="syntax"></a>Синтаксис
```
set root=<RootServer>
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                   Описание                                    |
|-----------------|----------------------------------------------------------------------------------|
|  <RootServer>   | Указывает новое имя для корневого сервера. Значение по умолчанию — ns.nic.ddn.mil. |
| {Help &#124;?} |              Отображает краткую сводку подкоманд **nslookup** .               |

## <a name="remarks"></a>Примечания
- Подкоманда **set root** влияет на **корневую** подкоманду.
  ## <a name="additional-references"></a>Дополнительные ссылки
  - [Command-Line Syntax Key](command-line-syntax-key.md)
  [Корневой раздел nslookup](nslookup-root.md) синтаксиса командной строки
