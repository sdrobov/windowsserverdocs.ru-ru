---
title: пользователь FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0a77bfeb-27a9-4f2f-a3c4-2fef529fb569 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cb4f0f47f23bec312c57266479c261c96535e8cc
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725064"
---
# <a name="ftp-user"></a>FTP: пользователь

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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

## <a name="examples"></a>Примеры  
Укажите Пользователь1 с паролем password1.  
```  
user User1 Password1  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
