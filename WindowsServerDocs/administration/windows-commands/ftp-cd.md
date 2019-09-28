---
title: компакт-диск FTP
description: Раздел команд Windows для компакт-диска FTP
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a574855a-31b4-45c6-bce2-581c7231c99b vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 891b144b20ebbef6c7e8058771d8249f4bace1cc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376491"
---
# <a name="ftp-cd"></a>FTP: CD

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет рабочий каталог на удаленном компьютере.   
## <a name="syntax"></a>Синтаксис  
```  
cd <remotedirectory>  
```  
### <a name="parameters"></a>Параметры  

|     Параметр     |                                 Описание                                 |
|-------------------|-----------------------------------------------------------------------------|
| <remotedirectory> | Указывает каталог на удаленном компьютере, который необходимо изменить. |

## <a name="BKMK_Examples"></a>Примеров  
Измените каталог на удаленном компьютере на **документы**.  
```  
cd Docs  
```  
Измените каталог на удаленном компьютере, чтобы он **мог получить видео**.  
```  
cd  May Videos  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
