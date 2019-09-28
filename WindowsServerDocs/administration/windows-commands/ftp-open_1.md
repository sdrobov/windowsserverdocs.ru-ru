---
title: open_1 FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b61926a-dc60-4b4c-96d3-64e5c91c18ba vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c5da1c73362c0396300f712b2e45b906d1652604
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376191"
---
# <a name="ftp-open_1"></a>FTP: open_1

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Подключается к указанному FTP-серверу.   
## <a name="syntax"></a>Синтаксис  
```  
open <computer> [<Port>]  
```  
### <a name="parameters"></a>Параметры  

| Параметр  |                                           Описание                                            |
|------------|--------------------------------------------------------------------------------------------------|
| <computer> |                Указывает удаленный компьютер, к которому вы пытаетесь подключиться.                 |
|  [<Port>]  | Указывает номер порта TCP, используемый для подключения к FTP-серверу. По умолчанию используется TCP-порт 21. |

## <a name="remarks"></a>Примечания  
Можно использовать IP-адрес или имя компьютера (в этом случае должен быть доступен DNS-сервер или файл Hosts) для указания **компьютера**.  
## <a name="BKMK_Examples"></a>Примеров  
Подключитесь к FTP-серверу по адресу **FTP.Microsoft.com**.  
```  
Open ftp.microsoft.com  
```  
Подключитесь к FTP-серверу по адресу **FTP.Microsoft.com** , который прослушивает TCP-порт 755.  
```  
open ftp.microsoft.com 755  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
