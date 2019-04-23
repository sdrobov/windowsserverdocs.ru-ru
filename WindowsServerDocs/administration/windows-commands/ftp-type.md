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
ms.openlocfilehash: 3524c7c772cdcd54a131d8a7e8c8714fad9ce563
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858905"
---
# <a name="ftp-type"></a>FTP: тип

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает или отображает тип передачи файла.   
## <a name="syntax"></a>Синтаксис  
```  
type [<typeName>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|[<typeName>]|Указывает тип передачи файла.|  
## <a name="remarks"></a>Примечания  
-   Если *typeName* не указан, отображается текущий тип.  
-   **FTP** поддерживает две файл типы перемещения, ASCII и двоичный файл.  
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
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
