---
title: Тип FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6e96dcd4-08f8-4e7b-90b7-1e1761fea4c7 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 36a80fd251794d9bec993d0366551cdc71a4cdf0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842867"
---
# <a name="ftp-type"></a>FTP: тип

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает или отображает тип перемещения файла.   
## <a name="syntax"></a>Синтаксис  
```  
type [<typeName>]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |            Описание            |
|--------------|-----------------------------------|
| [<typeName>] | Указывает тип перемещения файла. |

## <a name="remarks"></a>Примечания  
- Если параметр *TypeName* не указан, отображается текущий тип.  
- **протокол FTP** поддерживает два типа передач файлов: ASCII и binary.  
  Тип перемещения файла по умолчанию — ASCII.  При передаче текстовых файлов следует использовать команду **ASCII** . В режиме ASCII выполняется преобразование символов в стандартную сетевую кодировку и из нее. Например, символы конца строки преобразуются как обязательные в зависимости от операционной системы в месте назначения.  
  При передаче исполняемых файлов следует использовать **двоичную** команду. В двоичном режиме файл перемещается в однобайтовые единицы.  
  ## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
  Задайте для параметра тип перемещения файла значение ASCII.  
  ```  
  type ascii  
  ```  
  Задайте тип файла для перемещения binary.  
  ```  
  type binary  
  ```  
  ## <a name="additional-references"></a>Дополнительные материалы  
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
