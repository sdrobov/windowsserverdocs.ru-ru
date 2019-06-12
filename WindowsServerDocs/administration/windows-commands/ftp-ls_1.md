---
title: FTP ls_1
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e03c7db-1e2b-419c-acb2-8a68f3db9615 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6abf8466f90ac29846f2e1ee7d305e7e4280231e
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438635"
---
# <a name="ftp-ls1"></a>ftp: ls_1

> Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012
> 
> 
> Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Вывод сокращенного списка файлов и подкаталогов с удаленного компьютера.   
## <a name="syntax"></a>Синтаксис  
```  
ls [<remotedirectory>] [<LocalFile>]  
```  
### <a name="parameters"></a>Параметры  

|      Параметр      |                                                                       Описание                                                                        |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<remotedirectory>] | Указывает каталог, для которого требуется просмотреть список. Если каталог не указан, используется текущий рабочий каталог на удаленном компьютере. |
|    [<LocalFile>]    |               Указывает локальный файл, в котором для сохранения списка. Если локальный файл не указан, результаты отображаются на экране.               |

## <a name="BKMK_Examples"></a>Примеры  
Отображение сокращенного списка файлов и подкаталогов с удаленного компьютера.  
```  
ls  
```  
Получить сокращенный список каталогов **dir1** на удаленном компьютере и сохраните его в локальном файле называется **файл**  
```  
ls dir1 dirlist.txt   
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
