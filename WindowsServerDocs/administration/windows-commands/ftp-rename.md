---
title: Переименование FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 977b7c95-6428-4980-80ec-79c3ae7e8c4d vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 977baa042a6b0d9c23db7cb398bee997c2049227
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376025"
---
# <a name="ftp-rename"></a>FTP: Rename

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Переименовывает удаленные файлы.   
## <a name="syntax"></a>Синтаксис  
```  
rename <FileName> <NewFileName>  
```  
### <a name="parameters"></a>Параметры  

|   Параметр   |                 Описание                 |
|---------------|---------------------------------------------|
|  <FileName>   | Указывает файл, который требуется переименовать. |
| <NewFileName> |        Указывает новое имя файла.         |

## <a name="BKMK_Examples"></a>Примеров  
Переименуйте удаленный файл **example. txt** в **example1. txt.**  
```  
rename example.txt example1.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
