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
ms.openlocfilehash: 9390f8e5b0bded92a553b3057d122dace3fc665a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59851615"
---
# <a name="ftp-mdelete1"></a>ftp: mdelete_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет файлы на удаленном компьютере.   
## <a name="syntax"></a>Синтаксис  
```  
mdelete <remoteFile>[ ]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<remoteFile>|Указывает удаленный файл для удаления.|  
## <a name="BKMK_Examples"></a>Примеры  
Удалить удаленные файлы **a.exe** и **b.exe**.  
```  
mdelete a.exe b.exe  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
