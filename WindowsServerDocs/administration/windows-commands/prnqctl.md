---
title: prnqctl
description: Печать тестовой страницы, приостановка или возобновление печати принтера.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 189b344dc0c4f587ba7a6382c481304242e22c74
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372039"
---
# <a name="prnqctl"></a>prnqctl

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Печать тестовой страницы, приостановка или возобновление печати принтера и очистка очереди печати.  

## <a name="syntax"></a>Синтаксис  
```  
cscript Prnqctl {-z | -m | -e | -x | -?} [-s <ServerName>]   
[-p <printerName>] [-u <UserName>] [-w <Password>]  
```  
## <a name="parameters"></a>Параметры  

|Параметр|Описание|  
|-------|--------|  
|– z|приостанавливает печать на принтере, указанном параметром **-p** .|  
|-m|Возобновляет печать на принтере, указанном параметром **-p** .|  
|-e|выводит тестовую страницу на принтере, указанном параметром **-p** .|  
|-x|Отменяет все задания печати на принтере, указанном параметром **-p** .|  
|-s \<ServerName >|Указывает имя удаленного компьютера, на котором размещен принтер, которым требуется управлять. Если компьютер не указан, используется локальный компьютер.|  
|-p @no__t — 0printerName >|Указывает имя принтера, которым требуется управлять. Обязательный.|  
|-u \<UserName >-w \<Password >|Указывает учетную запись с разрешениями на подключение к компьютеру, на котором размещен принтер, которым требуется управлять. Все члены локальной группы администраторов целевого компьютера имеют эти разрешения, но разрешения также могут быть предоставлены другим пользователям. Если учетная запись не указана, необходимо войти в систему с учетной записью с этими разрешениями, чтобы команда работала.|  
|/?|Отображение справки в командной строке.|  

## <a name="remarks"></a>Примечания  
- Команда **прнкктл** является сценарием Visual Basic, расположенным в каталоге%WINdir%\System32\printing_Admin_Scripts @ no__t-1 @ no__t-2. Чтобы использовать эту команду, в командной строке введите **cscript** , а затем полный путь к файлу прнкктл или измените каталоги на соответствующую папку. Пример:  
  ```  
  cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prnqctl  
  ```  
- Если предоставленные сведения содержат пробелы, заключите его в кавычки (например, `"computer Name"`).  

## <a name="BKMK_examples"></a>Примеров  
Чтобы напечатать тестовую страницу на принтере Laserprinter1, предоставленном на компьютере \\ \ Server1, введите:  
```  
cscript Prnqctl -e -s Server1 -p Laserprinter1  
```  
Чтобы приостановить печать на принтере Laserprinter1 на локальном компьютере, введите:  
```  
cscript Prnqctl -z -p Laserprinter1  
```  
Чтобы отменить все задания печати на принтере Laserprinter1 на локальном компьютере, введите:  
```  
cscript Prnqctl -x -p Laserprinter1  
```  

#### <a name="additional-references"></a>Дополнительные ссылки  
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
[Справочник по командам печати](print-command-reference.md)  
