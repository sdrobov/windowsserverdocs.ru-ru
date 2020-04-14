---
title: получение по FTP
description: Раздел команд Windows для FTP Get
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d70355c4-58ef-43e0-916b-c7ecf77e6ee4 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c0b4dc41ec29edfb94661176a5ccaf651584fc43
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843487"
---
# <a name="ftp-get"></a>FTP: Get

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует удаленный файл на локальный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
get <remoteFile> [<LocalFile>]  
```  
#### <a name="parameters"></a>Параметры  

|   Параметр   |                                                              Описание                                                               |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------|
| <remoteFile>  |                                                   Указывает удаленный файл для копирования.                                                   |
| [<LocalFile>] | Указывает имя файла, используемого на локальном компьютере. Если параметр *локальный_файл* не указан, файлу присваивается имя *ремотефиле* . |

## <a name="remarks"></a>Примечания  
Команда **Get** идентична команде **recv** .  
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Скопируйте файл **Test. txt** на локальный компьютер, используя текущий тип перемещения файлов.  
```  
get test.txt  
```  
Скопируйте файл **Test. txt** на локальный компьютер в файле **test1. txt** , используя текущий тип перемещения файлов.  
```  
Get test.txt test1.txt  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   [FTP: ASCII](ftp-ascii.md)  
-   [FTP: двоичный формат](ftp-binary.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
