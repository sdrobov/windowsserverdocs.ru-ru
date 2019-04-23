---
title: пользователь FTP
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: ef3b943491a90078dab453aaf3a037bd4ccf1825
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59887495"
---
# <a name="ftp-user"></a>FTP: пользователь

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Указывает пользователя к удаленному компьютеру.   
## <a name="syntax"></a>Синтаксис  
```  
user <UserName> [<Password>] [<Account>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<UserName>|Указывает имя пользователя для подключения к удаленному компьютеру.|  
|[<Password>]|Указывает пароль для *UserName*. Если пароль не указан, но требуется, **ftp** запрашивает пароль.|  
|[<Account>]|Указывает учетную запись для входа на удаленном компьютере. Если *учетной записи* не указан, но требуется, **ftp** запрашивает для учетной записи.|  
## <a name="BKMK_Examples"></a>Примеры  
Укажите пароль Password1 User1.  
```  
user User1 Password1  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
