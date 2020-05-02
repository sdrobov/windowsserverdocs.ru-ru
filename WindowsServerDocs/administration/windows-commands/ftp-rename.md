---
title: Переименование FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 977b7c95-6428-4980-80ec-79c3ae7e8c4d vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5dc5006c82df8417a8652a9c0ba20f7f1a002e7f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725113"
---
# <a name="ftp-rename"></a>FTP: Rename

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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

## <a name="examples"></a>Примеры  
Переименуйте удаленный файл **example. txt** в **example1. txt.**  
```  
rename example.txt example1.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
