---
title: nslookup root
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9c29edc3-ec49-43f2-bc49-86bf0612d816
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bdfbe40443cf8f2fec2f81608bb93603cd74937f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723694"
---
# <a name="nslookup-root"></a>nslookup root

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет сервер по умолчанию на сервер для корня пространства имен домена службы доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
root 
```
### <a name="parameters"></a>Параметры

|    Параметр    |                      Описание                      |
|-----------------|-------------------------------------------------------|
| {Help &#124;?} | Отображает краткую сводку подкоманд **nslookup** . |

## <a name="remarks"></a>Примечания
- В настоящее время используется сервер имен ns.nic.ddn.mil. Эта команда является синонимом для лсервер ns.nic.ddn.mil. Имя корневого сервера можно изменить с помощью команды **set root** .
  ## <a name="additional-references"></a>Дополнительные ссылки
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [nslookup set root](nslookup-set-root.md)
