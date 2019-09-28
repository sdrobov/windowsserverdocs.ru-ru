---
title: пользователь FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a77bfeb-27a9-4f2f-a3c4-2fef529fb569 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 63281a0ffdd646d3652eb3a442a8edd9acec9cce
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375866"
---
# <a name="ftp-user"></a>FTP: пользователь

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Указывает пользователя для удаленного компьютера.   
## <a name="syntax"></a>Синтаксис  
```  
user <UserName> [<Password>] [<Account>]  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |                                                                      Описание                                                                      |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <UserName>  |                                          Указывает имя пользователя для входа на удаленный компьютер.                                           |
| [<Password>] |               Указывает пароль для *имени пользователя*. Если пароль не указан, но является обязательным, **FTP** запрашивает пароль.               |
| [<Account>]  | Указывает учетную запись для входа на удаленный компьютер. Если *учетная запись* не указана, но является обязательной, **FTP** запрашивает учетную запись. |

## <a name="BKMK_Examples"></a>Примеров  
Укажите Пользователь1 с паролем password1.  
```  
user User1 Password1  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
