---
title: FTP ASCII
description: Справочный раздел по FTP ASCII
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 523be48e-eab0-4237-8fb5-ca222824f0b6 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: aa33637f43ef8d26635f36b40dbd21cfe2bff42e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725396"
---
# <a name="ftp-ascii"></a>FTP: ASCII

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает тип перемещения файла ASCII.   
## <a name="syntax"></a>Синтаксис  
```  
ascii  
```  
#### <a name="parameters"></a>Параметры  
none  
## <a name="remarks"></a>Примечания  
- Тип перемещения файла по умолчанию — ASCII.  
- В режиме ASCII выполняется преобразование символов в стандартную сетевую кодировку и из нее. Например, символы конца строки при необходимости преобразуются в зависимости от целевой операционной системы.  
- **протокол FTP** поддерживает как ASCII, так и двоичные файлы изображений. При передаче текстовых файлов используйте ASCII. Дополнительные сведения о переносе двоичных файлов см. в разделе **FTP: двоичные** файлы в дополнительных ссылках.  
  ## <a name="examples"></a>Примеры  
  Задайте для параметра тип перемещения файла значение ASCII.  
  ```  
  ascii  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [FTP: двоичный формат](ftp-binary.md)  
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
