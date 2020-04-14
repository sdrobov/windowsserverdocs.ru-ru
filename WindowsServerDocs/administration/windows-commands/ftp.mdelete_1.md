---
title: mdelete_1 FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8a80a8f5-e880-40a8-abc9-29a41836844f vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9b64fa691a9ac890aad0e8d8dc93bd73e53478fc
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842727"
---
# <a name="ftp-mdelete_1"></a>FTP: mdelete_1

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет файлы на удаленном компьютере.   
## <a name="syntax"></a>Синтаксис  
```  
mdelete <remoteFile>[ ]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |             Описание              |
|--------------|--------------------------------------|
| <remoteFile> | Указывает удаленный файл для удаления. |

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Удаление удаленных файлов **a. exe** и **b. exe**.  
```  
mdelete a.exe b.exe  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
