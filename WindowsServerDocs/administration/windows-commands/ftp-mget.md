---
title: MGET FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 666025c92b6fb1a612cbe7b83833557a8a7d5017
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376298"
---
# <a name="ftp-mget"></a>FTP: mget

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует удаленные файлы на локальный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
mget <remoteFile>[ ]  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |                        Описание                        |
|--------------|-----------------------------------------------------------|
| <remoteFile> | Указывает удаленные файлы, которые необходимо скопировать на локальный компьютер. |

## <a name="BKMK_Examples"></a>Примеров  
Скопируйте удаленные файлы **a. exe** и **b. exe** на локальный компьютер, используя текущий тип перемещения файлов.  
```  
mget a.exe b.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ASCII](ftp-ascii.md)  
-   [FTP: двоичный формат](ftp-binary.md)  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
