---
title: mls_1 FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: a84a0f8f3121ea19876744e9ef04bebf5f9fcb08
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376261"
---
# <a name="ftp-mls_1"></a>FTP: mls_1

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сокращенный список файлов и подкаталогов в удаленном каталоге.   
## <a name="syntax"></a>Синтаксис  
```  
mls <remoteFile>[ ] <LocalFile>  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |                       Описание                       |
|--------------|---------------------------------------------------------|
| <remoteFile> | Указывает файл, для которого требуется просмотреть список. |
| <LocalFile>  |  Указывает локальный файл для хранения списка.  |

## <a name="remarks"></a>Примечания  
- Указание *ремотефилес*  
  Введите дефис ( **-** ), чтобы использовать текущий рабочий каталог на удаленном компьютере.  
- Указание параметра *локальный_файл*  
  Введите дефис ( **-** ) для отображения списка на экране.  
  ## <a name="BKMK_Examples"></a>Примеров  
  Отображение сокращенного списка файлов и подкаталогов для **Dir1** и **Dir2**.  
  ```  
  mls dir1 dir2 -  
  ```  
  Сохраните сокращенный список файлов и подкаталогов для **Dir1** и **Dir2** в локальном файле **дирлист. txt.**  
  ```  
  mls dir1 dir2 dirlist.txt   
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
