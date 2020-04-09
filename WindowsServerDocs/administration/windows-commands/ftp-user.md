---
title: пользователь FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0a77bfeb-27a9-4f2f-a3c4-2fef529fb569 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 29081bd8c5d537e1f060e4c848b720a60b4c8aea
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842857"
---
# <a name="ftp-user"></a>FTP: пользователь

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Указывает пользователя для удаленного компьютера.   
## <a name="syntax"></a>Синтаксис  
```  
user <UserName> [<Password>] [<Account>]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |                                                                      Описание                                                                      |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <UserName>  |                                          Указывает имя пользователя для входа на удаленный компьютер.                                           |
| [<Password>] |               Указывает пароль для *имени пользователя*. Если пароль не указан, но является обязательным, **FTP** запрашивает пароль.               |
| [<Account>]  | Указывает учетную запись для входа на удаленный компьютер. Если *учетная запись* не указана, но является обязательной, **FTP** запрашивает учетную запись. |

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Укажите Пользователь1 с паролем password1.  
```  
user User1 Password1  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
