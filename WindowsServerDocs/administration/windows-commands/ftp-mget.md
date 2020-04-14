---
title: MGET FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6c85ae96-ec51-48a9-a227-7f02c7332c69 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 72b45f84622fcd6abf7a743f606fb514def584cd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843357"
---
# <a name="ftp-mget"></a>FTP: mget

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует удаленные файлы на локальный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
mget <remoteFile>[ ]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |                        Описание                        |
|--------------|-----------------------------------------------------------|
| <remoteFile> | Указывает удаленные файлы, которые необходимо скопировать на локальный компьютер. |

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Скопируйте удаленные файлы **a. exe** и **b. exe** на локальный компьютер, используя текущий тип перемещения файлов.  
```  
mget a.exe b.exe  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   [FTP: ASCII](ftp-ascii.md)  
-   [FTP: двоичный формат](ftp-binary.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
