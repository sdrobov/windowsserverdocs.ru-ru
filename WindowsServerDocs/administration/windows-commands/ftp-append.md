---
title: Добавление в FTP
description: 'Раздел команд Windows для добавления по FTP '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c1a133c-31dc-41a4-9eb9-258efd79804d vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 52d16b878ff5fb165fd851b227dcc361c9da3a80
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376645"
---
# <a name="ftp-append"></a>FTP: Append

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

добавляет локальный файл в файл на удаленном компьютере, используя текущий параметр типа файла.   
## <a name="syntax"></a>Синтаксис  
```  
append <LocalFile> [remoteFile]  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |                               Описание                                |
|--------------|--------------------------------------------------------------------------|
| <LocalFile>  |                     Указывает локальный файл для добавления.                     |
| [Ремотефиле] | Указывает файл на удаленном компьютере, к которому добавляется <LocalFile>. |

## <a name="remarks"></a>Примечания  
Если *ремотефиле* опущен, то вместо имени удаленного файла будет использоваться имя *локальный_файл* .  
## <a name="BKMK_Examples"></a>Примеров  
Добавьте file1. txt в file2. txt на удаленном компьютере.  
```  
append file1.txt file2.txt  
```  
Добавьте локальный файл file1. txt к файлу с именем file1. txt на удаленном компьютере.  
```  
append file1.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
