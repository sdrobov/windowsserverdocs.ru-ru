---
title: Откройте Telnet
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e30ad68c-2366-4754-ac36-311a2392902a vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a87c4bac000a63af806705e9371a79d7370a34c1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59838245"
---
# <a name="telnet-open"></a>Telnet: открыть

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Подключается к серверу telnet.    
## <a name="syntax"></a>Синтаксис  
```  
o[pen] <hostname> [<Port>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<hostname>|Указывает имя компьютера или IP-адрес.|  
|[<Port>]|Задает TCP-порт, который прослушивает сервер telnet. По умолчанию используется TCP-порт 23.|  
## <a name="BKMK_Examples"></a>Примеры  
Подключиться к серверу telnet telnet.microsoft.com.  
```  
o telnet.microsoft.com  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
