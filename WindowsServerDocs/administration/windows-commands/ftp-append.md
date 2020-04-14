---
title: Добавление в FTP
description: Раздел команд Windows для добавления по FTP
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c1a133c-31dc-41a4-9eb9-258efd79804d vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 44ce1d6e7259dc8745da35ed462e6378f0fce8ba
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843827"
---
# <a name="ftp-append"></a>FTP: Append

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

добавляет локальный файл в файл на удаленном компьютере, используя текущий параметр типа файла.   
## <a name="syntax"></a>Синтаксис  
```  
append <LocalFile> [remoteFile]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |                               Описание                                |
|--------------|--------------------------------------------------------------------------|
| <LocalFile>  |                     Указывает локальный файл для добавления.                     |
| [Ремотефиле] | Указывает файл на удаленном компьютере, к которому добавляется <LocalFile>. |

## <a name="remarks"></a>Примечания  
Если *ремотефиле* опущен, то вместо имени удаленного файла будет использоваться имя *локальный_файл* .  
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Добавьте file1. txt в file2. txt на удаленном компьютере.  
```  
append file1.txt file2.txt  
```  
Добавьте локальный файл file1. txt к файлу с именем file1. txt на удаленном компьютере.  
```  
append file1.txt  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
