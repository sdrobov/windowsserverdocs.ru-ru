---
title: Telnet не задано
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da9a0d99-1930-4858-93c7-0e9c3797ee09 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 37c4d84d1664fdc13ea7ffec60bf981b264dba00
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59853895"
---
# <a name="telnet-unset"></a>Telnet: отменить задание

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отключает ранее параметры set.   
## <a name="syntax"></a>Синтаксис  
```  
u[nset] {bsasdel | crlf | delasbs | escape | localecho | logging | ntlm} [?]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|bsasdel|Отправляет **Backspace** как **Backspace**.|  
|CRLF|Отправляет **ввод** ключа как CR. Также называется режим перевода строки.|  
|delasbs|Отправляет **удалить** как **удалить**.|  
|escape|Удаляет параметр символ escape.|  
|локального|Включение, отключение локального.|  
|logging|Отключает ведение журнала.|  
|NTLM|Отключает проверку подлинности NTLM.|  
|?|Отображает справку для этой команды.|  
## <a name="BKMK_Examples"></a>Примеры  
Отключите ведение журнала.  
```  
u logging  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
