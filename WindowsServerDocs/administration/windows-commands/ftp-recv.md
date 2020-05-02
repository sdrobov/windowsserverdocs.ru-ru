---
title: FTP recv
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f249ce61-247d-421b-9b93-48bce5108800 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5ece259f2d48e18f6a789d51b1df7089490f2fa1
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725120"
---
# <a name="ftp-recv"></a>FTP: recv

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует удаленный файл на локальный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
recv <remoteFile> [<LocalFile>]  
```  
#### <a name="parameters"></a>Параметры  

|   Параметр   |                   Описание                    |
|---------------|--------------------------------------------------|
| <remoteFile>  |        Указывает удаленный файл для копирования.        |
| [<LocalFile>] | Указывает имя, используемое на локальном компьютере. |

## <a name="remarks"></a>Примечания  
- Команда **recv** идентична команде **Get** .  
- Если параметр *локальный_файл* не указан, файлу присваивается имя *ремотефиле* .  
  ## <a name="examples"></a>Примеры  
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
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
