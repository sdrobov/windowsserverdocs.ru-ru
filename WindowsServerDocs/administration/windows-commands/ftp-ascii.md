---
title: FTP ASCII
description: Раздел команд Windows для FTP ASCII
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 523be48e-eab0-4237-8fb5-ca222824f0b6 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c4930d0d726acaa222f802d7aaef59578030db5f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843787"
---
# <a name="ftp-ascii"></a>FTP: ASCII

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает тип перемещения файла ASCII.   
## <a name="syntax"></a>Синтаксис  
```  
ascii  
```  
#### <a name="parameters"></a>Параметры  
нет  
## <a name="remarks"></a>Примечания  
- Тип перемещения файла по умолчанию — ASCII.  
- В режиме ASCII выполняется преобразование символов в стандартную сетевую кодировку и из нее. Например, символы конца строки при необходимости преобразуются в зависимости от целевой операционной системы.  
- **протокол FTP** поддерживает как ASCII, так и двоичные файлы изображений. При передаче текстовых файлов используйте ASCII. Дополнительные сведения о переносе двоичных файлов см. в разделе **FTP: двоичные** файлы в дополнительных ссылках.  
  ## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
  Задайте для параметра тип перемещения файла значение ASCII.  
  ```  
  ascii  
  ```  
  ## <a name="additional-references"></a>Дополнительные материалы  
- [FTP: двоичный формат](ftp-binary.md)  
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
