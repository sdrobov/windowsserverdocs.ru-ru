---
title: двоичный файл FTP
description: Раздел команд Windows для двоичного файла FTP
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ee925b4d-85d2-47b1-b7d6-3832b7ec5505 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 20b2f72517826576cfee643eda0c54063b162c94
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843727"
---
# <a name="ftp-binary"></a>FTP: двоичный формат

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает тип перемещения файла binary.   
## <a name="syntax"></a>Синтаксис  
```  
binary  
```  
#### <a name="parameters"></a>Параметры  
нет  
## <a name="remarks-optional-section"></a>Примечания <optional section>  
**протокол FTP** поддерживает как ASCII, так и двоичные файлы изображений. Используйте двоичный формат при передаче исполняемых файлов. В двоичном режиме файлы передаются в однобайтовых единицах. Дополнительные сведения о переносе файлов ASCII см. в разделе **FTP: ASCII** в дополнительных ссылках.  
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Задайте для параметра тип перемещения файла значение двоичный.  
```  
binary  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   [FTP: ASCII](ftp-ascii.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
