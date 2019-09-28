---
title: мдир FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90eec45b-558b-4b8d-bbe4-b56d98e1ca70 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 08aa5bb216a3d0155c100c761e476bb963e59311
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375851"
---
# <a name="ftp-mdir"></a>FTP: мдир

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает список каталогов файлов и подкаталогов в удаленном каталоге.   
## <a name="syntax"></a>Синтаксис  
```  
mdir <remoteFile>[ ] <LocalFile>  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |                               Описание                                |
|--------------|--------------------------------------------------------------------------|
| <remoteFile> |   Указывает каталог или файл, для которого требуется просмотреть список.   |
| <LocalFile>  | Указывает локальный файл для хранения списка. Это обязательный параметр. |

## <a name="remarks"></a>Примечания  
- **Мдир** можно использовать для указания нескольких файлов.  
- Указание *ремотефиле*  
  Введите дефис ( **-** ), чтобы использовать текущий рабочий каталог на удаленном компьютере.  
- Задание параметра *локальный_файл*  
  Введите дефис ( **-** ) для отображения списка на экране.  
  ## <a name="BKMK_Examples"></a>Примеров  
  Отображение списка каталогов **Dir1** и **Dir2** на экране  
  ```  
  mdir dir1 dir2 -  
  ```  
  Сохраните Объединенный каталог со списком **Dir1** и **Dir2** в локальном файле с именем **дирлист. txt.**  
  ```  
  mdir dir1 dir2 dirlist.txt  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
