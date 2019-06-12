---
title: Переименование FTP
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 977b7c95-6428-4980-80ec-79c3ae7e8c4d vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 80d1a15f038017444c7654a44748bfd22be8e487
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438380"
---
# <a name="ftp-rename"></a>FTP: переименование

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Переименование удаленных файлов.   
## <a name="syntax"></a>Синтаксис  
```  
rename <FileName> <NewFileName>  
```  
### <a name="parameters"></a>Параметры  

|   Параметр   |                 Описание                 |
|---------------|---------------------------------------------|
|  <FileName>   | Указывает файл, который требуется переименовать. |
| <NewFileName> |        Указывает новое имя файла.         |

## <a name="BKMK_Examples"></a>Примеры  
Переименуйте файл удаленного **example.txt** для **example1.txt**  
```  
rename example.txt example1.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
