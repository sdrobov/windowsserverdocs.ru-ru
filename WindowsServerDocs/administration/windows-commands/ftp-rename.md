---
title: Переименование FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 977b7c95-6428-4980-80ec-79c3ae7e8c4d vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bbe159f2833ce52921b46e46881a1d7aed8c5df8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843027"
---
# <a name="ftp-rename"></a>FTP: Rename

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Переименовывает удаленные файлы.   
## <a name="syntax"></a>Синтаксис  
```  
rename <FileName> <NewFileName>  
```  
#### <a name="parameters"></a>Параметры  

|   Параметр   |                 Описание                 |
|---------------|---------------------------------------------|
|  <FileName>   | Указывает файл, который требуется переименовать. |
| <NewFileName> |        Указывает новое имя файла.         |

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Переименуйте удаленный файл **example. txt** в **example1. txt.**  
```  
rename example.txt example1.txt  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
