---
title: Отправка Telnet
description: Раздел команд Windows для Telnet Send, который отправляет команды Telnet на сервер Telnet.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c217abc-1182-466e-914c-1ff16755021b vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6fef48ca04a3817f58d063bc8b23f5c11c4ea197
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833287"
---
# <a name="telnet-send"></a>Telnet: send

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отправляет команды Telnet на сервер Telnet.   

## <a name="syntax"></a>Синтаксис  
```  
sen[d] {ao | ayt | brk | esc | ip | synch | <string>} [?]  
```  
#### <a name="parameters"></a>Параметры  

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

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Отправьте их на сервер Telnet.  
```  
sen ayt  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
