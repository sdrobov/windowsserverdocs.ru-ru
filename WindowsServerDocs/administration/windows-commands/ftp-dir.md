---
title: FTP dir
description: Раздел команд Windows для FTP dir
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: c47971c52135d79ce62f935bfed981f6eefcecaa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376441"
---
# <a name="ftp-dir"></a>FTP: dir

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает список файлов каталога и подкаталогов на удаленном компьютере.   
## <a name="syntax"></a>Синтаксис  
```  
dir [<remotedirectory>] [<LocalFile>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|[<remotedirectory>]|Указывает каталог, для которого требуется просмотреть список. Если каталог не указан, используется текущий рабочий каталог на удаленном компьютере.|  
|[<LocalFile>]|Указывает локальный файл, в котором будет храниться список каталогов. Если локальный файл не указан, результаты отображаются на экране.|  
## <a name="BKMK_Examples"></a>Примеров  
Отображение списка каталогов для **Dir1** на удаленном компьютере.  
```  
dir dir1  
```  
Сохраните список текущего каталога на удаленном компьютере в локальном файле **дирлист. txt**.  
```  
dir . dirlist.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
