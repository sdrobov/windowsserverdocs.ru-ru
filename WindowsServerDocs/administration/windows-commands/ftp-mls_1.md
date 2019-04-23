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
ms.openlocfilehash: 6cf81018fa590d38e55778d60b0cb0e849ab83de
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59835705"
---
# <a name="ftp-mls1"></a>FTP: mls_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Вывод сокращенного списка файлов и подкаталогов в удаленном каталоге.   
## <a name="syntax"></a>Синтаксис  
```  
mls <remoteFile>[ ] <LocalFile>  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<remoteFile>|Указывает файл, для которого требуется просмотреть список.|  
|<LocalFile>|Указывает локальный файл, в котором для сохранения списка.|  
## <a name="remarks"></a>Примечания  
-   Указание *Удаленных_файлов*  
    Введите дефис (**-**) использовать текущий рабочий каталог на удаленном компьютере.  
-   Указание *Локальный_файл*  
    Введите дефис (**-**) для вывода списка на экране.  
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
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
