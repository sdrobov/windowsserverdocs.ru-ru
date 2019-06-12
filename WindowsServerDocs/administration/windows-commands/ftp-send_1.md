---
title: FTP send_1
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 39423aff3c64f41c4fc0f8998484e6dcc38f822e
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438442"
---
# <a name="ftp-send1"></a>ftp: send_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальный файл на удаленный компьютер, используя текущий тип передачи файла.   
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
- **Отправки** команда идентична **поместить** команды.  
- Если *Удаленный_файл* не указан, будет использовано *Локальный_файл* имя.  
  ## <a name="BKMK_Examples"></a>Примеры  
  скопировать локальный файл **test.txt** и назовите его **test1.txt** на удаленном компьютере.  
  ```  
  send test.txt test1.txt  
  ```  
  скопировать локальный файл **program.exe** к удаленному компьютеру.  
  ```  
  send program.exe  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
