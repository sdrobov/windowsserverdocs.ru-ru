---
title: мдир FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90eec45b-558b-4b8d-bbe4-b56d98e1ca70 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: afb024d063761f1e817f02fdd7301376dd167846
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842717"
---
# <a name="ftp-mdir"></a>FTP: мдир

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает список каталогов файлов и подкаталогов в удаленном каталоге.   
## <a name="syntax"></a>Синтаксис  
```  
mdir <remoteFile>[ ] <LocalFile>  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |                               Описание                                |
|--------------|--------------------------------------------------------------------------|
| <remoteFile> |   Указывает каталог или файл, для которого требуется просмотреть список.   |
| <LocalFile>  | Указывает локальный файл для хранения списка. Этот параметр обязателен. |

## <a name="remarks"></a>Примечания  
- **Мдир** можно использовать для указания нескольких файлов.  
- Указание *ремотефиле*  
  Введите дефис ( **-** ), чтобы использовать текущий рабочий каталог на удаленном компьютере.  
- Задание параметра *локальный_файл*  
  Введите дефис ( **-** ) для отображения списка на экране.  
  ## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
  Отображение списка каталогов **Dir1** и **Dir2** на экране  
  ```  
  mdir dir1 dir2 -  
  ```  
  Сохраните Объединенный каталог со списком **Dir1** и **Dir2** в локальном файле с именем **дирлист. txt.**  
  ```  
  mdir dir1 dir2 dirlist.txt  
  ```  
  ## <a name="additional-references"></a>Дополнительные материалы  
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
