---
title: send_1 FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 000aa80a-60a0-4b51-815f-3237a4f3e0f4 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bd9f658b4fbfa5f6c9fa9a58fb0c524ad53627bc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375997"
---
# <a name="ftp-send_1"></a>FTP: send_1

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальный файл на удаленный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
send <LocalFile> [<remoteFile>]  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |                    Описание                    |
|--------------|---------------------------------------------------|
| <LocalFile>  |         Указывает локальный файл для копирования.         |
| <remoteFile> | Указывает имя, используемое на удаленном компьютере. |

## <a name="remarks"></a>Примечания  
- Команда **Send** идентична команде **размещения** .  
- Если *ремотефиле* не указан, файлу присваивается имя *локальный_файл* .  
  ## <a name="BKMK_Examples"></a>Примеров  
  Скопируйте локальный файл **Test. txt** и назовите его **test1. txt** на удаленном компьютере.  
  ```  
  send test.txt test1.txt  
  ```  
  Скопируйте локальный файл **Program. exe** на удаленный компьютер.  
  ```  
  send program.exe  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
