---
title: двоичный файл FTP
description: Справочный раздел для двоичного файла FTP
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ee925b4d-85d2-47b1-b7d6-3832b7ec5505 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 60a3e84bf9256dd5c71dd4444b5939980eecc512
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725370"
---
# <a name="ftp-binary"></a>FTP: двоичный формат

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает тип перемещения файла binary.   
## <a name="syntax"></a>Синтаксис  
```  
binary  
```  
#### <a name="parameters"></a>Параметры  
none  
## <a name="remarks-optional-section"></a>Примечания<optional section>  
**протокол FTP** поддерживает как ASCII, так и двоичные файлы изображений. Используйте двоичный формат при передаче исполняемых файлов. В двоичном режиме файлы передаются в однобайтовых единицах. Дополнительные сведения о переносе файлов ASCII см. в разделе **FTP: ASCII** в дополнительных ссылках.  
## <a name="examples"></a>Примеры  
Задайте для параметра тип перемещения файла значение двоичный.  
```  
binary  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ASCII](ftp-ascii.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
