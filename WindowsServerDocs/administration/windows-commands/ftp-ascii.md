---
title: FTP ASCII
description: 'Раздел команд Windows для FTP ASCII '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: d5ae0064f9c1679bb8b386271f042d589b158c73
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376617"
---
# <a name="ftp-ascii"></a>FTP: ASCII

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает тип перемещения файла ASCII.   
## <a name="syntax"></a>Синтаксис  
```  
ascii  
```  
### <a name="parameters"></a>Параметры  
none  
## <a name="remarks"></a>Примечания  
- Тип перемещения файла по умолчанию — ASCII.  
- В режиме ASCII выполняется преобразование символов в стандартную сетевую кодировку и из нее. Например, символы конца строки при необходимости преобразуются в зависимости от целевой операционной системы.  
- **протокол FTP** поддерживает как ASCII, так и двоичные файлы изображений. При передаче текстовых файлов используйте ASCII. Дополнительные сведения о переносе двоичных файлов см. в разделе **FTP: двоичные** файлы в дополнительных ссылках.  
  ## <a name="BKMK_Examples"></a>Примеров  
  Задайте для параметра тип перемещения файла значение ASCII.  
  ```  
  ascii  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [FTP: двоичный формат](ftp-binary.md)  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
