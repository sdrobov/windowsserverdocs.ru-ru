---
title: FTP send_1
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 000aa80a-60a0-4b51-815f-3237a4f3e0f4 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3dca11f0d534eb875a71fa2c39cdd4dc674ad788
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862125"
---
# <a name="ftp-send1"></a>ftp: send_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальный файл на удаленный компьютер, используя текущий тип передачи файла.   
## <a name="syntax"></a>Синтаксис  
```  
send <LocalFile> [<remoteFile>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<LocalFile>|Указывает локальный файл для копирования.|  
|<remoteFile>|Указывает имя, используемое на удаленном компьютере.|  
## <a name="remarks"></a>Примечания  
-   **Отправки** команда идентична **поместить** команды.  
-   Если *Удаленный_файл* не указан, будет использовано *Локальный_файл* имя.  
## <a name="BKMK_Examples"></a>Примеры  
скопировать локальный файл **test.txt** и назовите его **test1.txt** на удаленном компьютере.  
```  
send test.txt test1.txt  
```  
скопировать локальный файл **program.exe** к удаленному компьютеру.  
```  
send program.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
