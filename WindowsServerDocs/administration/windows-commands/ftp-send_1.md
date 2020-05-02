---
title: send_1 FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 000aa80a-60a0-4b51-815f-3237a4f3e0f4 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 04617246c05edde127db01ce1a0fe692eb0aceb1
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725110"
---
# <a name="ftp-send_1"></a>FTP: send_1

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальный файл на удаленный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
send <LocalFile> [<remoteFile>]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |                    Описание                    |
|--------------|---------------------------------------------------|
| <LocalFile>  |         Указывает локальный файл для копирования.         |
| <remoteFile> | Указывает имя, используемое на удаленном компьютере. |

## <a name="remarks"></a>Примечания  
- Команда **Send** идентична команде **размещения** .  
- Если *ремотефиле* не указан, файлу присваивается имя *локальный_файл* .  
  ## <a name="examples"></a>Примеры  
  Скопируйте локальный файл **Test. txt** и назовите его **test1. txt** на удаленном компьютере.  
  ```  
  send test.txt test1.txt  
  ```  
  Скопируйте локальный файл **Program. exe** на удаленный компьютер.  
  ```  
  send program.exe  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
