---
title: Тип FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: eb254d1c9b17ac6baadf6b84702d2812f1117a93
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375897"
---
# <a name="ftp-type"></a>FTP: тип

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает или отображает тип перемещения файла.   
## <a name="syntax"></a>Синтаксис  
```  
type [<typeName>]  
```  
### <a name="parameters"></a>Параметры  

|  Параметр   |            Описание            |
|--------------|-----------------------------------|
| [<typeName>] | Указывает тип перемещения файла. |

## <a name="remarks"></a>Примечания  
- Если параметр *TypeName* не указан, отображается текущий тип.  
- **протокол FTP** поддерживает два типа передач файлов: ASCII и binary.  
  Тип перемещения файла по умолчанию — ASCII.  При передаче текстовых файлов следует использовать команду **ASCII** . В режиме ASCII выполняется преобразование символов в стандартную сетевую кодировку и из нее. Например, символы конца строки преобразуются как обязательные в зависимости от операционной системы в месте назначения.  
  При передаче исполняемых файлов следует использовать **двоичную** команду. В двоичном режиме файл перемещается в однобайтовые единицы.  
  ## <a name="BKMK_Examples"></a>Примеров  
  Задайте для параметра тип перемещения файла значение ASCII.  
  ```  
  type ascii  
  ```  
  Задайте тип файла для перемещения binary.  
  ```  
  type binary  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
