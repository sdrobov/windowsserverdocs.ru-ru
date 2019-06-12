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
ms.openlocfilehash: e43bf8b6e7067a31b3ec51336b0b43845ab88f63
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438598"
---
# <a name="ftp-mget"></a>FTP: mget

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Тип переноса копирует файлы с удаленного на локальный компьютер, с помощью текущего файла.   
## <a name="syntax"></a>Синтаксис  
```  
mget <remoteFile>[ ]  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |                        Описание                        |
|--------------|-----------------------------------------------------------|
| <remoteFile> | Указывает удаленные файлы для копирования на локальный компьютер. |

## <a name="BKMK_Examples"></a>Примеры  
Скопируйте удаленные файлы **a.exe** и **b.exe** на локальном компьютере, с помощью текущего типа передачи файлов.  
```  
mget a.exe b.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ascii](ftp-ascii.md)  
-   [FTP: двоичные](ftp-binary.md)  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
