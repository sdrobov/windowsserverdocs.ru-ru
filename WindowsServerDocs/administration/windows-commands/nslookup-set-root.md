---
title: nslookup set root
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 38cd5a2e9878a8e43393befc5cbd4fc47c65ec53
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436600"
---
# <a name="nslookup-set-root"></a>nslookup set root

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет имя корневого сервера, используемого для запросов.
## <a name="syntax"></a>Синтаксис
```
set root=<RootServer>
```
## <a name="parameters"></a>Параметры

|    Параметр    |                                   Описание                                    |
|-----------------|----------------------------------------------------------------------------------|
|  <RootServer>   | Указывает новое имя для корневого сервера. Значение по умолчанию — ns.nic.ddn.mil. |
| {help &#124; ?} |              Отображает краткое описание **nslookup** подкоманды.               |

## <a name="remarks"></a>Примечания
- **Корневой набор** подкоманды влияет на **корневой** подкоманды.
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса команд](command-line-syntax-key.md)
  [корневой nslookup](nslookup-root.md)
