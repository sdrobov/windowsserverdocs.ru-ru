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
ms.openlocfilehash: 99b938618deb2d1e779fd20c504c01a13a2d3f8a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868165"
---
# <a name="ftp-mput1"></a>ftp: mput_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Тип переноса копирование файлов на удаленный компьютер, с помощью текущего файла.   
## <a name="syntax"></a>Синтаксис  
```  
mput <LocalFile>[ ]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<LocalFile>|Указывает локальный файл для копирования на удаленный компьютер.|  
## <a name="BKMK_Examples"></a>Примеры  
Копировать **Program1.exe** и **Program2.exe** к удаленному компьютеру с помощью текущего типа передачи файлов.  
```  
mput Program1.exe Program2.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ascii](ftp-ascii.md)  
-   [FTP: двоичные](ftp-binary.md)  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
