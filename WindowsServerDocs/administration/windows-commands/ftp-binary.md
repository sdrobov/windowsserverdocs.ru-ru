---
title: двоичный файл FTP
description: Раздел команд Windows для двоичного файла FTP
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee925b4d-85d2-47b1-b7d6-3832b7ec5505 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 48579523f44232dec3357a20e8082050cc5175e6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376581"
---
# <a name="ftp-binary"></a>FTP: двоичный формат

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает тип перемещения файла binary.   
## <a name="syntax"></a>Синтаксис  
```  
binary  
```  
### <a name="parameters"></a>Параметры  
none  
## <a name="remarks-optional-section"></a>Примечания <optional section>  
**протокол FTP** поддерживает как ASCII, так и двоичные файлы изображений. Используйте двоичный формат при передаче исполняемых файлов. В двоичном режиме файлы передаются в однобайтовых единицах. Дополнительные сведения о переносе файлов ASCII см. в разделе **FTP: ASCII** в дополнительных ссылках.  
## <a name="BKMK_Examples"></a>Примеров  
Задайте для параметра тип перемещения файла значение двоичный.  
```  
binary  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: ASCII](ftp-ascii.md)  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
