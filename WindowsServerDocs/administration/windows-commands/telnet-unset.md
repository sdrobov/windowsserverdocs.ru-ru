---
title: Telnet не определено
description: Команды Windows для Telnet не имеют значения, что отключает ранее установленные параметры.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: da9a0d99-1930-4858-93c7-0e9c3797ee09 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 34d52eedb2a5547ad0e3f2912dbe2a250eaf8fc5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833147"
---
# <a name="telnet-unset"></a>Telnet: не задано

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отключает ранее установленные параметры.   

## <a name="syntax"></a>Синтаксис  
```  
u[nset] {bsasdel | crlf | delasbs | escape | localecho | logging | ntlm} [?]  
```  
#### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|бсасдел|Отправляет **Backspace** в виде **Backspace**.|  
|CRLF|Отправляет клавишу **Ввод** в виде CR. Также называется режимом перевода строки.|  
|деласбс|Отправляет **Удаление** как **Удаление**.|  
|escape-знак|Удаляет параметр escape-символа.|  
|локалечо|Отключает локалечо.|  
|ведение журналов|Отключает ведение журнала.|  
|NTLM|Отключает проверку подлинности NTLM.|  
|?|Отображает справку для этой команды.|  
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Отключите ведение журнала.  
```  
u logging  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
