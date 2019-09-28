---
title: mput_1 FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 980f15e7-7cf1-4813-9946-a8cc4edfb198 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6308f7b47d58bc25d964944f96fbc83a26350962
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376214"
---
# <a name="ftp-mput_1"></a>FTP: mput_1

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальные файлы на удаленный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
mput <LocalFile>[ ]  
```  
### <a name="parameters"></a>Параметры  

|  Параметр  |                       Описание                        |
|-------------|----------------------------------------------------------|
| <LocalFile> | Указывает локальный файл для копирования на удаленный компьютер. |

## <a name="BKMK_Examples"></a>Примеров  
Скопируйте **Program1. exe** и **Program2. exe** на удаленный компьютер, используя текущий тип перемещения файлов.  
```  
mput Program1.exe Program2.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ASCII](ftp-ascii.md)  
-   [FTP: двоичный формат](ftp-binary.md)  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
