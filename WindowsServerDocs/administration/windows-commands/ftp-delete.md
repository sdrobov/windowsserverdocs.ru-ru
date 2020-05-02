---
title: Удаление FTP
description: Справочный раздел по FTP-удалению
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 067c45f3-e4e8-4450-b8b6-836994f6adfe vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 14e4e870bb7f0f384e3803d75021298d04a8ca4d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725323"
---
# <a name="ftp-delete"></a>FTP: Delete

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет файлы на удаленных компьютерах.   
## <a name="syntax"></a>Синтаксис  
```  
delete <remoteFile>  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |          Описание          |
|--------------|-------------------------------|
| <remoteFile> | Указывает файл для удаления. |

## <a name="examples"></a>Примеры  
Удалите файл Test. txt на удаленном компьютере.  
```  
delete test.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
