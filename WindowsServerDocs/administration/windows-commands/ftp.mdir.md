---
title: Команда mdir FTP
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 0ac1e7cd50fe4d9325c272f74a7b81971c8bb12a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59878215"
---
# <a name="ftp-mdir"></a>ftp: mdir

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает список каталогов, файлов и подкаталогов в удаленном каталоге.   
## <a name="syntax"></a>Синтаксис  
```  
mdir <remoteFile>[ ] <LocalFile>  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<remoteFile>|Указывает каталог или файл, для которого требуется просмотреть список.|  
|<LocalFile>|Задает локальный файл для сохранения списка. Это обязательный параметр.|  
## <a name="remarks"></a>Примечания  
-   Можно использовать **mdir из** для указания нескольких файлов.  
-   Указание *Удаленный_файл*  
    Введите дефис (**-**) использовать текущий рабочий каталог на удаленном компьютере.  
-   Указание *Локальный_файл*  
    Введите дефис (**-**) для вывода списка на экране.  
## <a name="BKMK_Examples"></a>Примеры  
Отобразить список каталогов **dir1** и **dir2** на экране  
```  
mdir dir1 dir2 -  
```  
Сохранить объединенный список каталогов **dir1** и **dir2** в локальный файл с именем **файл**  
```  
mdir dir1 dir2 dirlist.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
