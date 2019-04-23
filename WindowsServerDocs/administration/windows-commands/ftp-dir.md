---
title: каталог FTP
description: Разделе команд Windows, для ftp-dir
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a29a92a5-7b79-4e6e-95cf-2ccb38bb6fb2 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 78ac8ac5e9fc4894f55401bb234aa98de981adf7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59835255"
---
# <a name="ftp-dir"></a>FTP: dir

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Список каталогов файлов и подкаталогов на удаленном компьютере.   
## <a name="syntax"></a>Синтаксис  
```  
dir [<remotedirectory>] [<LocalFile>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|[<remotedirectory>]|Указывает каталог, для которого требуется просмотреть список. Если каталог не указан, используется текущий рабочий каталог на удаленном компьютере.|  
|[<LocalFile>]|Указывает локальный файл, в которой будут храниться в каталоге. Если локальный файл не указан, результаты отображаются на экране.|  
## <a name="BKMK_Examples"></a>Примеры  
Отобразить список каталогов для **dir1** на удаленном компьютере.  
```  
dir dir1  
```  
Сохранение списка текущий каталог на удаленном компьютере в локальном файле **файл**.  
```  
dir . dirlist.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
