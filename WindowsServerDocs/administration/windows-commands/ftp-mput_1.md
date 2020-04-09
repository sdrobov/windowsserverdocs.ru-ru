---
title: mput_1 FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 980f15e7-7cf1-4813-9946-a8cc4edfb198 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 489e18da937e12a1fc69e0ee84d9dda00309ccd6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843237"
---
# <a name="ftp-mput_1"></a>FTP: mput_1

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальные файлы на удаленный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
mput <LocalFile>[ ]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр  |                       Описание                        |
|-------------|----------------------------------------------------------|
| <LocalFile> | Указывает локальный файл для копирования на удаленный компьютер. |

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Скопируйте **Program1. exe** и **Program2. exe** на удаленный компьютер, используя текущий тип перемещения файлов.  
```  
mput Program1.exe Program2.exe  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   [FTP: ASCII](ftp-ascii.md)  
-   [FTP: двоичный формат](ftp-binary.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
