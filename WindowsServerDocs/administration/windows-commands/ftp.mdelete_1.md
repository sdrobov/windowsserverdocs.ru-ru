---
title: mdelete_1 FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8a80a8f5-e880-40a8-abc9-29a41836844f vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f578a50207439f9bfb21c2607f0aa60a20fad292
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725029"
---
# <a name="ftp-mdelete_1"></a>FTP: mdelete_1

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет файлы на удаленном компьютере.   
## <a name="syntax"></a>Синтаксис  
```  
mdelete <remoteFile>[ ]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |             Описание              |
|--------------|--------------------------------------|
| <remoteFile> | Указывает удаленный файл для удаления. |

## <a name="examples"></a>Примеры  
Удаление удаленных файлов **a. exe** и **b. exe**.  
```  
mdelete a.exe b.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
