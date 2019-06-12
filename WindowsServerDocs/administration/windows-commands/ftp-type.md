---
title: Тип FTP
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e96dcd4-08f8-4e7b-90b7-1e1761fea4c7 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a261382da47501b416fa83c6d2497deae5711bb1
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438357"
---
# <a name="ftp-type"></a>FTP: тип

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает или отображает тип передачи файла.   
## <a name="syntax"></a>Синтаксис  
```  
type [<typeName>]  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |            Описание            |
|--------------|-----------------------------------|
| [<typeName>] | Указывает тип передачи файла. |

## <a name="remarks"></a>Примечания  
- Если *typeName* не указан, отображается текущий тип.  
- **FTP** поддерживает две файл типы перемещения, ASCII и двоичный файл.  
  Тип передачи файла по умолчанию — ASCII.  **Ascii** команда должна использоваться при передаче текстовых файлов. В этом режиме выполняются преобразования символов в и из набора стандартных символов сети. Например, символ окончания строки преобразуются как обязательные, на основе операционной системы в месте назначения.  
  **Двоичных** команда должна использоваться при передаче исполняемых файлов. В двоичном режиме файл перемещается в байту.  
  ## <a name="BKMK_Examples"></a>Примеры  
  Задайте тип передачи файла в ASCII.  
  ```  
  type ascii  
  ```  
  Задайте передачу тип файла в двоичный формат.  
  ```  
  type binary  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
