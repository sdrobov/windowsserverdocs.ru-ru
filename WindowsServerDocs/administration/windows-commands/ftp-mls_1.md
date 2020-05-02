---
title: mls_1 FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4738fd49-0e80-4bdf-a773-0f973db3a710 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 27f74d4c1d03cb4d9f665566f69485e80f8eccdc
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725203"
---
# <a name="ftp-mls_1"></a>FTP: mls_1

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сокращенный список файлов и подкаталогов в удаленном каталоге.   
## <a name="syntax"></a>Синтаксис  
```  
mls <remoteFile>[ ] <LocalFile>  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |                       Описание                       |
|--------------|---------------------------------------------------------|
| <remoteFile> | Указывает файл, для которого требуется просмотреть список. |
| <LocalFile>  |  Указывает локальный файл для хранения списка.  |

## <a name="remarks"></a>Примечания  
- Указание *ремотефилес*  
  Введите дефис (**-**), чтобы использовать текущий рабочий каталог на удаленном компьютере.  
- Указание параметра *локальный_файл*  
  Введите дефис (**-**) для отображения списка на экране.  
  ## <a name="examples"></a>Примеры  
  Отображение сокращенного списка файлов и подкаталогов для **Dir1** и **Dir2**.  
  ```  
  mls dir1 dir2 -  
  ```  
  Сохраните сокращенный список файлов и подкаталогов для **Dir1** и **Dir2** в локальном файле **дирлист. txt.**  
  ```  
  mls dir1 dir2 dirlist.txt   
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
