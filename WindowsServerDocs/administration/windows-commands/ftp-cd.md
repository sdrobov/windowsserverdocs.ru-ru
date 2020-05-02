---
title: компакт-диск FTP
description: Справочный раздел по FTP CD
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a574855a-31b4-45c6-bce2-581c7231c99b vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6fff0d9aaddddede2c61c1fc8708ae9e0f995083
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725342"
---
# <a name="ftp-cd"></a>FTP: CD

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет рабочий каталог на удаленном компьютере.   
## <a name="syntax"></a>Синтаксис  
```  
cd <remotedirectory>  
```  
#### <a name="parameters"></a>Параметры  

|     Параметр     |                                 Описание                                 |
|-------------------|-----------------------------------------------------------------------------|
| <remotedirectory> | Указывает каталог на удаленном компьютере, который необходимо изменить. |

## <a name="examples"></a>Примеры  
Измените каталог на удаленном компьютере на **документы**.  
```  
cd Docs  
```  
Измените каталог на удаленном компьютере, чтобы он **мог получить видео**.  
```  
cd  May Videos  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
