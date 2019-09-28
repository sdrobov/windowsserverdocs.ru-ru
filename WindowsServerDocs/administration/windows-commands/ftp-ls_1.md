---
title: ls_1 FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: d183f6a014273b78befd14c8d3208508948ffc54
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376250"
---
# <a name="ftp-ls_1"></a>FTP: ls_1

> Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012
> 
> 
> Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сокращенный список файлов и подкаталогов с удаленного компьютера.   
## <a name="syntax"></a>Синтаксис  
```  
ls [<remotedirectory>] [<LocalFile>]  
```  
### <a name="parameters"></a>Параметры  

|      Параметр      |                                                                       Описание                                                                        |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<remotedirectory>] | Указывает каталог, для которого требуется просмотреть список. Если каталог не указан, используется текущий рабочий каталог на удаленном компьютере. |
|    [<LocalFile>]    |               Указывает локальный файл для хранения списка. Если локальный файл не указан, результаты отображаются на экране.               |

## <a name="BKMK_Examples"></a>Примеров  
Отображение сокращенного списка файлов и подкаталогов с удаленного компьютера.  
```  
ls  
```  
Получите сокращенный список каталогов **Dir1** на удаленном компьютере и сохраните его в локальном файле с именем **дирлист. txt.**  
```  
ls dir1 dirlist.txt   
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
