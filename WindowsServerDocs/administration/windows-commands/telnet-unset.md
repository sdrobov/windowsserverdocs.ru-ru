---
title: Telnet не определено
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: e6f0eb98c4168d2f664780dad42ca1aea5463d24
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383481"
---
# <a name="telnet-unset"></a>Telnet: не задано

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отключает ранее установленные параметры.   
## <a name="syntax"></a>Синтаксис  
```  
u[nset] {bsasdel | crlf | delasbs | escape | localecho | logging | ntlm} [?]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|бсасдел|Отправляет **Backspace** в виде **Backspace**.|  
|CRLF|Отправляет клавишу **Ввод** в виде CR. Также называется режимом перевода строки.|  
|деласбс|Отправляет **Удаление** как **Удаление**.|  
|Выполняет|Удаляет параметр escape-символа.|  
|локалечо|Отключает локалечо.|  
|logging|Отключает ведение журнала.|  
|NTLM|Отключает проверку подлинности NTLM.|  
|?|Отображает справку для этой команды.|  
## <a name="BKMK_Examples"></a>Примеров  
Отключите ведение журнала.  
```  
u logging  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
