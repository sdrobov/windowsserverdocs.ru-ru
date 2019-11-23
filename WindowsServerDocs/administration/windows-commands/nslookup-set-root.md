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
ms.openlocfilehash: 5a1737275bf6321525bbba56cd4d6a77ef973423
ms.sourcegitcommit: 9a6a692a7b2a93f52bb9e2de549753e81d758d28
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72591027"
---
# <a name="nslookup-set-root"></a>nslookup set root

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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

## <a name="remarks"></a>Замечания
- Подкоманда **set root** влияет на **корневую** подкоманду.
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [корневой элемент nslookup](nslookup-root.md)
