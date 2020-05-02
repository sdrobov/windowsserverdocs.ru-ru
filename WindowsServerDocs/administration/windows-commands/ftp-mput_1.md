---
title: mput_1 FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 980f15e7-7cf1-4813-9946-a8cc4edfb198 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b3fb654d5a2f44b9b63238abdbaee8d6a0294861
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725221"
---
# <a name="ftp-mput_1"></a>FTP: mput_1

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальные файлы на удаленный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
mput <LocalFile>[ ]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр  |                       Описание                        |
|-------------|----------------------------------------------------------|
| <LocalFile> | Указывает локальный файл для копирования на удаленный компьютер. |

## <a name="examples"></a>Примеры  
Скопируйте **Program1. exe** и **Program2. exe** на удаленный компьютер, используя текущий тип перемещения файлов.  
```  
mput Program1.exe Program2.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ASCII](ftp-ascii.md)  
-   [FTP: двоичный формат](ftp-binary.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
