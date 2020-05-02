---
title: Добавление в FTP
description: Справочный раздел по добавлению по FTP
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c1a133c-31dc-41a4-9eb9-258efd79804d vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b53228473b8ea16a0955c244d60fae77cf4f7d7f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725403"
---
# <a name="ftp-append"></a>FTP: Append

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

добавляет локальный файл в файл на удаленном компьютере, используя текущий параметр типа файла.   
## <a name="syntax"></a>Синтаксис  
```  
append <LocalFile> [remoteFile]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |                               Описание                                |
|--------------|--------------------------------------------------------------------------|
| <LocalFile>  |                     Указывает локальный файл для добавления.                     |
| [Ремотефиле] | Указывает файл на удаленном компьютере, к которому <LocalFile> добавляется. |

## <a name="remarks"></a>Примечания  
Если *ремотефиле* опущен, то вместо имени удаленного файла будет использоваться имя *локальный_файл* .  
## <a name="examples"></a>Примеры  
Добавьте file1. txt в file2. txt на удаленном компьютере.  
```  
append file1.txt file2.txt  
```  
Добавьте локальный файл file1. txt к файлу с именем file1. txt на удаленном компьютере.  
```  
append file1.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
