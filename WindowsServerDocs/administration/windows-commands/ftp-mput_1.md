---
title: FTP mput_1
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: dd19a97246aa6155182cb055deceb4b5a5019f6c
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438579"
---
# <a name="ftp-mput1"></a>ftp: mput_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Тип переноса копирование файлов на удаленный компьютер, с помощью текущего файла.   
## <a name="syntax"></a>Синтаксис  
```  
mput <LocalFile>[ ]  
```  
### <a name="parameters"></a>Параметры  

|  Параметр  |                       Описание                        |
|-------------|----------------------------------------------------------|
| <LocalFile> | Указывает локальный файл для копирования на удаленный компьютер. |

## <a name="BKMK_Examples"></a>Примеры  
Копировать **Program1.exe** и **Program2.exe** к удаленному компьютеру с помощью текущего типа передачи файлов.  
```  
mput Program1.exe Program2.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ascii](ftp-ascii.md)  
-   [FTP: двоичные](ftp-binary.md)  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
