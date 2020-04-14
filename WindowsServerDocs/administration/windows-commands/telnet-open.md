---
title: открыть Telnet
description: Раздел команд Windows для Telnet Open, который подключается к серверу Telnet.
ms.prod: windows-server
ms.technology: manage-windows-commands
s.topic: article
ms.assetid: e30ad68c-2366-4754-ac36-311a2392902a vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b100d2b53a340a083f22d4fd88c42363642d5da5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833337"
---
# <a name="telnet-open"></a>Telnet: открыть

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Подключается к серверу Telnet.    

## <a name="syntax"></a>Синтаксис  
```  
o[pen] <hostname> [<Port>]  
```  
#### <a name="parameters"></a>Параметры  

| Параметр  |                                        Описание                                         |
|------------|--------------------------------------------------------------------------------------------|
| <hostname> |                         Указывает имя или IP-адрес компьютера.                         |
|  [<Port>]  | Указывает TCP-порт, который прослушивает сервер Telnet. Значение по умолчанию — TCP-порт 23. |

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Подключитесь к серверу Telnet по адресу telnet.microsoft.com.  
```  
o telnet.microsoft.com  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
