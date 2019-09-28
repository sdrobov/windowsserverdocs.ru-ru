---
title: mdelete_1 FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8a80a8f5-e880-40a8-abc9-29a41836844f vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6ffbb06cff9e177316ea60e281c25d7640a7f981
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375921"
---
# <a name="ftp-mdelete_1"></a>FTP: mdelete_1

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет файлы на удаленном компьютере.   
## <a name="syntax"></a>Синтаксис  
```  
mdelete <remoteFile>[ ]  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |             Описание              |
|--------------|--------------------------------------|
| <remoteFile> | Указывает удаленный файл для удаления. |

## <a name="BKMK_Examples"></a>Примеров  
Удаление удаленных файлов **a. exe** и **b. exe**.  
```  
mdelete a.exe b.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
