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
ms.openlocfilehash: 186664a75978f589a9a26047c72b9db74dd2dc4d
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66441125"
---
# <a name="telnet-open"></a>Telnet: открыть

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Подключается к серверу telnet.    
## <a name="syntax"></a>Синтаксис  
```  
o[pen] <hostname> [<Port>]  
```  
### <a name="parameters"></a>Параметры  

| Параметр  |                                        Описание                                         |
|------------|--------------------------------------------------------------------------------------------|
| <hostname> |                         Указывает имя компьютера или IP-адрес.                         |
|  [<Port>]  | Задает TCP-порт, который прослушивает сервер telnet. По умолчанию используется TCP-порт 23. |

## <a name="BKMK_Examples"></a>Примеры  
Подключиться к серверу telnet telnet.microsoft.com.  
```  
o telnet.microsoft.com  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
