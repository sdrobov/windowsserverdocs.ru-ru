---
title: получение по FTP
description: Раздел команд Windows для FTP Get
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d70355c4-58ef-43e0-916b-c7ecf77e6ee4 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4cc74b56fa849a25ed2f4e4a37d339b1da87c24f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376388"
---
# <a name="ftp-get"></a>FTP: Get

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует удаленный файл на локальный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
get <remoteFile> [<LocalFile>]  
```  
### <a name="parameters"></a>Параметры  

|   Параметр   |                                                              Описание                                                               |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------|
| <remoteFile>  |                                                   Указывает удаленный файл для копирования.                                                   |
| [<LocalFile>] | Указывает имя файла, используемого на локальном компьютере. Если параметр *локальный_файл* не указан, файлу присваивается имя *ремотефиле* . |

## <a name="remarks"></a>Примечания  
Команда **Get** идентична команде **recv** .  
## <a name="BKMK_Examples"></a>Примеров  
Скопируйте файл **Test. txt** на локальный компьютер, используя текущий тип перемещения файлов.  
```  
get test.txt  
```  
Скопируйте файл **Test. txt** на локальный компьютер в файле **test1. txt** , используя текущий тип перемещения файлов.  
```  
Get test.txt test1.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ASCII](ftp-ascii.md)  
-   [FTP: двоичный формат](ftp-binary.md)  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
