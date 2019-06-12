---
title: FTP mls_1
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4738fd49-0e80-4bdf-a773-0f973db3a710 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7a379ead9c56af096e121048a8c0f596f6879bb0
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438543"
---
# <a name="ftp-mls1"></a>FTP: mls_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Вывод сокращенного списка файлов и подкаталогов в удаленном каталоге.   
## <a name="syntax"></a>Синтаксис  
```  
mls <remoteFile>[ ] <LocalFile>  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |                       Описание                       |
|--------------|---------------------------------------------------------|
| <remoteFile> | Указывает файл, для которого требуется просмотреть список. |
| <LocalFile>  |  Указывает локальный файл, в котором для сохранения списка.  |

## <a name="remarks"></a>Примечания  
- Указание *Удаленных_файлов*  
  Введите дефис ( **-** ) использовать текущий рабочий каталог на удаленном компьютере.  
- Указание *Локальный_файл*  
  Введите дефис ( **-** ) для вывода списка на экране.  
  ## <a name="BKMK_Examples"></a>Примеры  
  Отображение сокращенного списка файлов и подкаталогов для **dir1** и **dir2**.  
  ```  
  mls dir1 dir2 -  
  ```  
  Сохранить сокращенный список файлов и подкаталогов для **dir1** и **dir2** в локальном файле **файл**  
  ```  
  mls dir1 dir2 dirlist.txt   
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
