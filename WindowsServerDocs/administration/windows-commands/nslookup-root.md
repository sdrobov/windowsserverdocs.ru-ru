---
title: nslookup root
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 3eb3375df3a109685fc8dc5d23f0c5008339d09e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373389"
---
# <a name="nslookup-root"></a>nslookup root

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет сервер по умолчанию на сервер для корня пространства имен домена службы доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
root 
```
## <a name="parameters"></a>Параметры

|    Параметр    |                      Описание                      |
|-----------------|-------------------------------------------------------|
| {Help &#124; ?} | Отображает краткую сводку подкоманд **nslookup** . |

## <a name="remarks"></a>Замечания
- В настоящее время используется сервер имен ns.nic.ddn.mil. Эта команда является синонимом для лсервер ns.nic.ddn.mil. Имя корневого сервера можно изменить с помощью команды **set root** .
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса командной строки
  команду](command-line-syntax-key.md) [nslookup set root](nslookup-set-root.md)
