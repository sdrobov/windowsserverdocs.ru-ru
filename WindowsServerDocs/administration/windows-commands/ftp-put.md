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
ms.openlocfilehash: 3307ba71e7b3c8b4113f9ed29ab06660dafa5f6f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868745"
---
# <a name="ftp-put"></a>FTP: put

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальный файл на удаленный компьютер, используя текущий тип передачи файла.   
## <a name="syntax"></a>Синтаксис  
```  
put <LocalFile> [<remoteFile>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<LocalFile>|Указывает локальный файл для копирования.|  
|[<remoteFile>]|Указывает имя, используемое на удаленном компьютере.|  
## <a name="remarks"></a>Примечания  
-   **Поместить** команда идентична **отправки** команды.  
-   Если *Удаленный_файл* не указан, будет использовано *Локальный_файл* имя.  
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
-   [FTP: ascii](ftp-ascii.md)  
-   [FTP: двоичные](ftp-binary.md)  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
