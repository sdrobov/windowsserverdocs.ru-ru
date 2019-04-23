---
title: Отправить Telnet
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c217abc-1182-466e-914c-1ff16755021b vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 32345b22395107f4a2c3d88894126d4e5e0875a1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842365"
---
# <a name="telnet-send"></a>Telnet: Отправка

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отправляет команды telnet на Telnet-сервер.   
## <a name="syntax"></a>Синтаксис  
```  
sen[d] {ao | ayt | brk | esc | ip | synch | <string>} [?]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|AO|Отправляет команду telnet прервать выходных данных.|  
|айт|Отправляет команды telnet являются вы существует.|  
|brk|Отправляет brk команды telnet.|  
|ESC|Отправляет текущий telnet escape-символ.|  
|IP-адрес|Отправляет команду telnet прерывания процесса.|  
|Синхронизация|Отправляет синхронизации команды telnet.|  
|<string>|Отправляет любой строки, введенные на Telnet-сервер.|  
|?|Отображает справку, связанную с помощью следующей команды.|  
## <a name="BKMK_Examples"></a>Примеры  
Send вы существует на Telnet-сервер.  
```  
sen ayt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
