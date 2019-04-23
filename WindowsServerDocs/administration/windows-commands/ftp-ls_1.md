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
ms.openlocfilehash: c45e26f6578510837f190ae20e3140e619dc59cb
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59841765"
---
# <a name="ftp-ls1"></a>ftp: ls_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012


>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Вывод сокращенного списка файлов и подкаталогов с удаленного компьютера.   
## <a name="syntax"></a>Синтаксис  
```  
ls [<remotedirectory>] [<LocalFile>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|[<remotedirectory>]|Указывает каталог, для которого требуется просмотреть список. Если каталог не указан, используется текущий рабочий каталог на удаленном компьютере.|  
|[<LocalFile>]|Указывает локальный файл, в котором для сохранения списка. Если локальный файл не указан, результаты отображаются на экране.|  
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
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
