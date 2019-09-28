---
title: Удаление FTP
description: Раздел команд Windows для FTP-удаления
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 067c45f3-e4e8-4450-b8b6-836994f6adfe vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1b566da14751921e2f38acd922ececbbc972daa6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376454"
---
# <a name="ftp-delete"></a>FTP: Delete

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет файлы на удаленных компьютерах.   
## <a name="syntax"></a>Синтаксис  
```  
delete <remoteFile>  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |          Описание          |
|--------------|-------------------------------|
| <remoteFile> | Указывает файл для удаления. |

## <a name="BKMK_Examples"></a>Примеров  
Удалите файл Test. txt на удаленном компьютере.  
```  
delete test.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
