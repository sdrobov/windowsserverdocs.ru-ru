---
title: Тип FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6e96dcd4-08f8-4e7b-90b7-1e1761fea4c7 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5531da30118914599ed0f85bfd10bd02ae89ffcf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725079"
---
# <a name="ftp-type"></a>FTP: тип

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает или отображает тип перемещения файла.   
## <a name="syntax"></a>Синтаксис  
```  
type [<typeName>]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |            Описание            |
|--------------|-----------------------------------|
| [<typeName>] | Определяет тип передачи файла. |

## <a name="remarks"></a>Примечания  
- Если параметр *TypeName* не указан, отображается текущий тип.  
- **протокол FTP** поддерживает два типа передач файлов: ASCII и binary.  
  Тип перемещения файла по умолчанию — ASCII.  При передаче текстовых файлов следует использовать команду **ASCII** . В режиме ASCII выполняется преобразование символов в стандартную сетевую кодировку и из нее. Например, символы конца строки преобразуются как обязательные в зависимости от операционной системы в месте назначения.  
  При передаче исполняемых файлов следует использовать **двоичную** команду. В двоичном режиме файл перемещается в однобайтовые единицы.  
  ## <a name="examples"></a>Примеры  
  Задайте для параметра тип перемещения файла значение ASCII.  
  ```  
  type ascii  
  ```  
  Задайте тип файла для перемещения binary.  
  ```  
  type binary  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
