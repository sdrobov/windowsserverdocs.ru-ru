---
title: двоичный FTP
description: Разделе команд Windows для двоичного файла с ftp
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee925b4d-85d2-47b1-b7d6-3832b7ec5505 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cadd59bff3bd2acf5c6d700caef66ca5c871b523
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821925"
---
# <a name="ftp-binary"></a>FTP: двоичные

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает тип передачи файла в двоичный формат.   
## <a name="syntax"></a>Синтаксис  
```  
binary  
```  
### <a name="parameters"></a>Параметры  
none  
## <a name="remarks-optional-section"></a>"Примечания" <optional section>  
**FTP** поддерживает как ASCII, так и типа двоичных файлов. Использовать двоичный формат, при передаче исполняемых файлов. В двоичном режиме файлы передаются в байту. Дополнительные сведения о передаче файлов ASCII, см. в разделе **ftp: ascii** в дополнительные ссылки.  
## <a name="BKMK_Examples"></a>Примеры  
Задайте тип передачи файла в двоичный формат.  
```  
binary  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ascii](ftp-ascii.md)  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
