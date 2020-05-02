---
title: MGET FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6c85ae96-ec51-48a9-a227-7f02c7332c69 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a71fbfb60ae012b5e65af04e6f3e21ec796996a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725236"
---
# <a name="ftp-mget"></a>FTP: mget

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует удаленные файлы на локальный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
mget <remoteFile>[ ]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |                        Описание                        |
|--------------|-----------------------------------------------------------|
| <remoteFile> | Указывает удаленные файлы, которые необходимо скопировать на локальный компьютер. |

## <a name="examples"></a>Примеры  
Скопируйте удаленные файлы **a. exe** и **b. exe** на локальный компьютер, используя текущий тип перемещения файлов.  
```  
mget a.exe b.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ASCII](ftp-ascii.md)  
-   [FTP: двоичный формат](ftp-binary.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
