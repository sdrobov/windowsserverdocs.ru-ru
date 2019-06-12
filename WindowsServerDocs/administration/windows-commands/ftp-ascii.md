---
title: FTP-ascii
description: 'Разделе команд Windows, для FTP-ascii '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 523be48e-eab0-4237-8fb5-ca222824f0b6 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8e38c57b7a5ffd9afe677c4b49787383412621fe
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438798"
---
# <a name="ftp-ascii"></a>ftp: ascii

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает тип передачи файла в ASCII.   
## <a name="syntax"></a>Синтаксис  
```  
ascii  
```  
### <a name="parameters"></a>Параметры  
none  
## <a name="remarks"></a>Примечания  
- Тип передачи файла по умолчанию — ASCII.  
- В этом режиме выполняются преобразования символов в и из набора стандартных символов сети. Например символ окончания строки преобразуются при необходимости, зависимости от целевой операционной системы.  
- **FTP** поддерживает как ASCII, так и типа двоичных файлов. Используйте ASCII, при передаче текстовых файлов. Дополнительные сведения о передаче двоичных файлов, см. в разделе **ftp: двоичный** в дополнительные ссылки.  
  ## <a name="BKMK_Examples"></a>Примеры  
  Задайте тип передачи файла в ASCII.  
  ```  
  ascii  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [FTP: двоичные](ftp-binary.md)  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
