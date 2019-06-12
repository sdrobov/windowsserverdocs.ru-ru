---
title: nslookup root
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c29edc3-ec49-43f2-bc49-86bf0612d816
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 47a26be99a5eee510970d3eee6b486331a98b159
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436906"
---
# <a name="nslookup-root"></a>nslookup root

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменение сервера по умолчанию на сервер для корневого пространства имен доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
root 
```
## <a name="parameters"></a>Параметры

|    Параметр    |                      Описание                      |
|-----------------|-------------------------------------------------------|
| {help &#124; ?} | Отображает краткое описание **nslookup** подкоманды. |

## <a name="remarks"></a>Примечания
- В настоящее время используется ns.nic.ddn.mil имя сервера. Эта команда является синонимом lserver ns.nic.ddn.mil. Можно изменить имя корневого сервера с **корневого набора** команды.
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса команд](command-line-syntax-key.md)
  [nslookup задать корень](nslookup-set-root.md)
