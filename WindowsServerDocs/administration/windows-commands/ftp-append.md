---
title: Добавление FTP
description: 'Добавьте в разделе команд Windows, для FTP-сервера '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c1a133c-31dc-41a4-9eb9-258efd79804d vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 23fa04b86d9c26fb30b74eebe8caef8498b90a12
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879035"
---
# <a name="ftp-append"></a>FTP: Добавление

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет локальный файл в файл на удаленном компьютере, с использованием текущих настроек типа файлов.   
## <a name="syntax"></a>Синтаксис  
```  
append <LocalFile> [remoteFile]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<LocalFile>|Задает имя локального файла для добавления.|  
|[Удаленный_файл]|Указывает файл на удаленном компьютере, к которому <LocalFile> добавляется.|  
## <a name="remarks"></a>Примечания  
Если *Удаленный_файл* опущен, *Локальный_файл* имя используется вместо имени удаленного файла.  
## <a name="BKMK_Examples"></a>Примеры  
Добавление file1.txt file2.txt на удаленном компьютере.  
```  
append file1.txt file2.txt  
```  
Добавление локального file1.txt в файл с именем file1.txt на удаленном компьютере.  
```  
append file1.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
