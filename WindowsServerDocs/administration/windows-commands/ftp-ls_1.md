---
title: ls_1 FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5e03c7db-1e2b-419c-acb2-8a68f3db9615 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5ff63272fe3c5e59965b04bef258a06fee2da0c4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843367"
---
# <a name="ftp-ls_1"></a>FTP: ls_1

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012
> 
> 
> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сокращенный список файлов и подкаталогов с удаленного компьютера.   
## <a name="syntax"></a>Синтаксис  
```  
ls [<remotedirectory>] [<LocalFile>]  
```  
#### <a name="parameters"></a>Параметры  

|      Параметр      |                                                                       Описание                                                                        |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<remotedirectory>] | Указывает каталог, для которого требуется просмотреть список. Если каталог не указан, используется текущий рабочий каталог на удаленном компьютере. |
|    [<LocalFile>]    |               Указывает локальный файл для хранения списка. Если локальный файл не указан, результаты отображаются на экране.               |

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Отображение сокращенного списка файлов и подкаталогов с удаленного компьютера.  
```  
ls  
```  
Получите сокращенный список каталогов **Dir1** на удаленном компьютере и сохраните его в локальном файле с именем **дирлист. txt.**  
```  
ls dir1 dirlist.txt   
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
