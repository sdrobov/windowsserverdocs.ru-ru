---
title: FTP recv
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f249ce61-247d-421b-9b93-48bce5108800 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6ec35a2044945e3d39a2a78d39923de3a56eb18d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376126"
---
# <a name="ftp-recv"></a>FTP: recv

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует удаленный файл на локальный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
recv <remoteFile> [<LocalFile>]  
```  
### <a name="parameters"></a>Параметры  

|   Параметр   |                   Описание                    |
|---------------|--------------------------------------------------|
| <remoteFile>  |        Указывает удаленный файл для копирования.        |
| [<LocalFile>] | Указывает имя, используемое на локальном компьютере. |

## <a name="remarks"></a>Примечания  
- Команда **recv** идентична команде **Get** .  
- Если параметр *локальный_файл* не указан, файлу присваивается имя *ремотефиле* .  
  ## <a name="BKMK_Examples"></a>Примеров  
  Скопируйте файл **Test. txt** на локальный компьютер, используя текущий тип перемещения файлов.  
  ```  
  recv test.txt  
  ```  
  Скопируйте файл **Test. txt** на локальный компьютер в файле **test1. txt** , используя текущий тип перемещения файлов.  
  ```  
  recv test.txt test1.txt  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [FTP: ASCII](ftp-ascii.md)  
- [FTP: двоичный формат](ftp-binary.md)  
- [FTP: Get](ftp-get.md)  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
