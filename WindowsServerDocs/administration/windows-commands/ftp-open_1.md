---
title: open_1 FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4b61926a-dc60-4b4c-96d3-64e5c91c18ba vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8bd3063a52908d65f336afcda6b6982d5bc9bf94
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843187"
---
# <a name="ftp-open_1"></a>FTP: open_1

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Подключается к указанному FTP-серверу.   
## <a name="syntax"></a>Синтаксис  
```  
open <computer> [<Port>]  
```  
#### <a name="parameters"></a>Параметры  

| Параметр  |                                           Описание                                            |
|------------|--------------------------------------------------------------------------------------------------|
| <computer> |                Указывает удаленный компьютер, к которому вы пытаетесь подключиться.                 |
|  [<Port>]  | Указывает номер порта TCP, используемый для подключения к FTP-серверу. По умолчанию используется TCP-порт 21. |

## <a name="remarks"></a>Примечания  
Можно использовать IP-адрес или имя компьютера (в этом случае должен быть доступен DNS-сервер или файл Hosts) для указания **компьютера**.  
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Подключитесь к FTP-серверу по адресу **FTP.Microsoft.com**.  
```  
Open ftp.microsoft.com  
```  
Подключитесь к FTP-серверу по адресу **FTP.Microsoft.com** , который прослушивает TCP-порт 755.  
```  
open ftp.microsoft.com 755  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
