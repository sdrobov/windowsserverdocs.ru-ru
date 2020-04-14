---
title: send_1 FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 000aa80a-60a0-4b51-815f-3237a4f3e0f4 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: df6ea9eda6fced91babca37639cd6efe981ba7de
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843007"
---
# <a name="ftp-send_1"></a>FTP: send_1

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальный файл на удаленный компьютер, используя текущий тип перемещения файлов.   
## <a name="syntax"></a>Синтаксис  
```  
send <LocalFile> [<remoteFile>]  
```  
#### <a name="parameters"></a>Параметры  

|  Параметр   |                    Описание                    |
|--------------|---------------------------------------------------|
| <LocalFile>  |         Указывает локальный файл для копирования.         |
| <remoteFile> | Указывает имя, используемое на удаленном компьютере. |

## <a name="remarks"></a>Примечания  
- Команда **Send** идентична команде **размещения** .  
- Если *ремотефиле* не указан, файлу присваивается имя *локальный_файл* .  
  ## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
  Скопируйте локальный файл **Test. txt** и назовите его **test1. txt** на удаленном компьютере.  
  ```  
  send test.txt test1.txt  
  ```  
  Скопируйте локальный файл **Program. exe** на удаленный компьютер.  
  ```  
  send program.exe  
  ```  
  ## <a name="additional-references"></a>Дополнительные материалы  
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
