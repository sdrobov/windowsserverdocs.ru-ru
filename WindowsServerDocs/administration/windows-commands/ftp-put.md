---
title: FTP-размещение
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95cc1e3f-523d-4374-98b8-16e6c276b2ca vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 15c1734322d3642ebc85891b71c6ad68100d514d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376071"
---
# <a name="ftp-put"></a>FTP: размещение

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальный файл на удаленный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
put <LocalFile> [<remoteFile>]  
```  
### <a name="parameters"></a>Параметры  

|   Параметр    |                    Описание                    |
|----------------|---------------------------------------------------|
|  <LocalFile>   |         Указывает локальный файл для копирования.         |
| [<remoteFile>] | Указывает имя, используемое на удаленном компьютере. |

## <a name="remarks"></a>Примечания  
- Команда **размещения** идентична команде **Send** .  
- Если *ремотефиле* не указан, файлу присваивается имя *локальный_файл* .  
  ## <a name="BKMK_Examples"></a>Примеров  
  Скопируйте локальный файл **Test. txt** и назовите его **test1. txt** на удаленном компьютере.  
  ```  
  put test.txt test1.txt  
  ```  
  Скопируйте локальный файл **Program. exe** на удаленный компьютер.  
  ```  
  put program.exe  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [FTP: ASCII](ftp-ascii.md)  
- [FTP: двоичный формат](ftp-binary.md)  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
