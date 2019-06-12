---
title: Поместите FTP
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 4d602c685b7eac5d18c88bc0f6709b189cc61a77
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438466"
---
# <a name="ftp-put"></a>FTP: put

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальный файл на удаленный компьютер, используя текущий тип передачи файла.   
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
- **Поместить** команда идентична **отправки** команды.  
- Если *Удаленный_файл* не указан, будет использовано *Локальный_файл* имя.  
  ## <a name="BKMK_Examples"></a>Примеры  
  скопировать локальный файл **test.txt** и назовите его **test1.txt** на удаленном компьютере.  
  ```  
  put test.txt test1.txt  
  ```  
  скопировать локальный файл **program.exe** к удаленному компьютеру.  
  ```  
  put program.exe  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [FTP: ascii](ftp-ascii.md)  
- [FTP: двоичные](ftp-binary.md)  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
