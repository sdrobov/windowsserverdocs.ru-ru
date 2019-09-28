---
title: Отправка Telnet
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 958e0e507e5a0ae836da98de8d677a116dbb38bd
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383635"
---
# <a name="telnet-send"></a>Telnet: send

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отправляет команды Telnet на сервер Telnet.   
## <a name="syntax"></a>Синтаксис  
```  
sen[d] {ao | ayt | brk | esc | ip | synch | <string>} [?]  
```  
### <a name="parameters"></a>Параметры  

| Параметр |                     Описание                      |
|-----------|------------------------------------------------------|
|    AO     |       Отправляет выходные данные команды Telnet Abort.        |
|    айт    |       Отправляет команду Telnet.       |
|    брк    |            Отправляет команду Telnet БРК.            |
|    ESC    |      Отправляет текущий escape-символ Telnet.      |
|    см     |     Отправляет процесс прерывания команды Telnet.     |
|   Синхронизация   |           Отправка команды Telnet Synch.           |
| <string>  | Отправляет любую строку, введенную на сервер Telnet. |
|     ?     |     Отображает справку, связанную с этой командой.      |

## <a name="BKMK_Examples"></a>Примеров  
Отправьте их на сервер Telnet.  
```  
sen ayt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
