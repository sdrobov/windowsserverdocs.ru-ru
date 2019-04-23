---
title: число полученных FTP
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f249ce61-247d-421b-9b93-48bce5108800 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4979010c13d78c89c9a3e4965b567f7eef1f2ede
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59841105"
---
# <a name="ftp-recv"></a>FTP: получаемого сообщения

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует удаленный файл на локальный компьютер, используя текущий тип передачи файла.   
## <a name="syntax"></a>Синтаксис  
```  
recv <remoteFile> [<LocalFile>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<remoteFile>|Задает удаленный файл для копирования.|  
|[<LocalFile>]|Указывает имя, используемое на локальном компьютере.|  
## <a name="remarks"></a>Примечания  
-   **Recv** команда идентична **получить** команды.  
-   Если *Локальный_файл* не указан, будет использовано *Удаленный_файл* имя.  
## <a name="BKMK_Examples"></a>Примеры  
Копировать **test.txt** на локальном компьютере, с помощью текущего типа передачи файлов.  
```  
recv test.txt  
```  
Копировать **test.txt** на локальном компьютере как **test1.txt** тип переноса с помощью текущего файла.  
```  
recv test.txt test1.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ascii](ftp-ascii.md)  
-   [FTP: двоичные](ftp-binary.md)  
-   [FTP: получение](ftp-get.md)  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
