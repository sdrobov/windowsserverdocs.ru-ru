---
title: prnqctl
description: Напечатайте тестовую страницу, приостановить или возобновить работу принтера.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8df9dfa7-984c-4276-bb7d-e7675e7c399e jpjofre
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 26af9527b7b16b42fd9d389f3409143dfc3e9aa9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858085"
---
# <a name="prnqctl"></a>prnqctl

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

пробную печать, приостанавливает или возобновляет работу принтера и очищает очередь принтера.  
  
## <a name="syntax"></a>Синтаксис  
```  
cscript Prnqctl {-z | -m | -e | -x | -?} [-s <ServerName>]   
[-p <printerName>] [-u <UserName>] [-w <Password>]  
```  
## <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|-z|Приостановка печати на принтер, указанный с помощью **-p** параметра.|  
|-m|Возобновляет печать на принтере, указанный с помощью **-p** параметра.|  
|-e|пробную печать на принтере, указанный с помощью **-p** параметра.|  
|-x|Отменяет все задания печати на принтер, указанный с помощью **-p** параметра.|  
|-s \<ServerName >|Задает имя удаленного компьютера, на котором размещена принтера, которое вы хотите управлять. Если компьютер не указан, используется локальный компьютер.|  
|-p \<Имя_принтера >|Задает имя используемого принтера, которое вы хотите управлять. Обязательный.|  
|-u \<UserName> -w \<Password>|Задает учетную запись с разрешениями на подключение к компьютеру, на котором размещена принтера, которое вы хотите управлять. Эти разрешения всех членов локальной группы администраторов на конечном компьютере, но можно также выделить разрешения другим пользователям. Если не указать учетную запись, вы должны войти в систему с учетной записью с этими разрешениями для команды для работы.|  
|/?|Отображение справки в командной строке.|  

## <a name="remarks"></a>Примечания  
-   **Prnqctl** команда — это сценарий Visual Basic, расположенный в %WINdir%\System32\printing_Admin_Scripts\\ <language> каталога. Чтобы использовать эту команду в командной строке, введите **cscript** следуют полный путь к файлу prnqctl, или изменить каталоги в соответствующую папку. Пример:  
    ```  
    cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prnqctl  
    ```  
-   Если сведения, которые вы предоставляете содержит пробелы, используйте кавычки вокруг текста (например, `"computer Name"`).  

## <a name="BKMK_examples"></a>Примеры  
Чтобы напечатать пробную страницу на Laserprinter1 общего принтера в \\\Server1 компьютера, введите:  
```  
cscript Prnqctl -e -s Server1 -p Laserprinter1  
```  
Чтобы приостановить печати на принтере Laserprinter1 на локальном компьютере, введите следующую команду:  
```  
cscript Prnqctl -z -p Laserprinter1  
```  
Чтобы отменить все задания печати на принтере Laserprinter1 на локальном компьютере, введите следующую команду:  
```  
cscript Prnqctl -x -p Laserprinter1  
```  

#### <a name="additional-references"></a>Дополнительные ссылки  
[Ключ синтаксиса командной строки](command-line-syntax-key.md)  
[Описание команды печати](print-command-reference.md)  
