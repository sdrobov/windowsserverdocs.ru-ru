---
title: мдир FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90eec45b-558b-4b8d-bbe4-b56d98e1ca70 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 54adcd1d28079487c5e238c72413d8269447944e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725026"
---
# <a name="ftp-mdir"></a>FTP: мдир

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает список каталогов файлов и подкаталогов в удаленном каталоге.   
## <a name="syntax"></a>Синтаксис  
```  
mdir <remoteFile>[ ] <LocalFile>  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |                               Описание                                |
|--------------|--------------------------------------------------------------------------|
| <remoteFile> |   Указывает каталог или файл, для которого требуется просмотреть список.   |
| <LocalFile>  | Указывает локальный файл для хранения списка. Это обязательный параметр. |

## <a name="remarks"></a>Примечания  
- **Мдир** можно использовать для указания нескольких файлов.  
- Указание *ремотефиле*  
  Введите дефис (**-**), чтобы использовать текущий рабочий каталог на удаленном компьютере.  
- Задание параметра *локальный_файл*  
  Введите дефис (**-**) для отображения списка на экране.  
  ## <a name="examples"></a>Примеры  
  Отображение списка каталогов **Dir1** и **Dir2** на экране  
  ```  
  mdir dir1 dir2 -  
  ```  
  Сохраните Объединенный каталог со списком **Dir1** и **Dir2** в локальном файле с именем **дирлист. txt.**  
  ```  
  mdir dir1 dir2 dirlist.txt  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
