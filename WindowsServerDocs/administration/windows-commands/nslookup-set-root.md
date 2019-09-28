---
title: nslookup set root
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ad5393c-d4fd-4594-8187-576b1dcde60a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 08cf41ec9b6ac30699013112216a538dcf625fd5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372845"
---
# <a name="nslookup-set-root"></a>nslookup set root

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет имя корневого сервера, используемого для запросов.
## <a name="syntax"></a>Синтаксис
```
set root=<RootServer>
```
## <a name="parameters"></a>Параметры

|    Параметр    |                                   Описание                                    |
|-----------------|----------------------------------------------------------------------------------|
|  <RootServer>   | Указывает новое имя для корневого сервера. Значение по умолчанию — ns.nic.ddn.mil. |
| {Help &#124; ?} |              Отображает краткую сводку подкоманд **nslookup** .               |

## <a name="remarks"></a>Примечания
- Подкоманда **set root** влияет на **корневую** подкоманду.
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [root nslookup](nslookup-root.md)
