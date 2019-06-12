---
title: ftp mdelete_1
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 7b342f9d728e91085d5edf2f8e1ece00b48bec8d
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438326"
---
# <a name="ftp-mdelete1"></a>ftp: mdelete_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет файлы на удаленном компьютере.   
## <a name="syntax"></a>Синтаксис  
```  
mdelete <remoteFile>[ ]  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |             Описание              |
|--------------|--------------------------------------|
| <remoteFile> | Указывает удаленный файл для удаления. |

## <a name="BKMK_Examples"></a>Примеры  
Удалить удаленные файлы **a.exe** и **b.exe**.  
```  
mdelete a.exe b.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
