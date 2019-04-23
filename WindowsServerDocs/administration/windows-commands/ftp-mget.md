---
title: FTP mget
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6c85ae96-ec51-48a9-a227-7f02c7332c69 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1160ec742dde318141da720bd35b7d60ab805bb1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59888425"
---
# <a name="ftp-mget"></a>FTP: mget

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Тип переноса копирует файлы с удаленного на локальный компьютер, с помощью текущего файла.   
## <a name="syntax"></a>Синтаксис  
```  
mget <remoteFile>[ ]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<remoteFile>|Указывает удаленные файлы для копирования на локальный компьютер.|  
## <a name="BKMK_Examples"></a>Примеры  
Скопируйте удаленные файлы **a.exe** и **b.exe** на локальном компьютере, с помощью текущего типа передачи файлов.  
```  
mget a.exe b.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ascii](ftp-ascii.md)  
-   [FTP: двоичные](ftp-binary.md)  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
