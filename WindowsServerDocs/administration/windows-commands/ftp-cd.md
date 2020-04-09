---
title: компакт-диск FTP
description: Раздел команд Windows для компакт-диска FTP
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a574855a-31b4-45c6-bce2-581c7231c99b vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9739a3dbfb2dcb350cf34e90ceaeb29360e53598
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843717"
---
# <a name="ftp-cd"></a>FTP: CD

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет рабочий каталог на удаленном компьютере.   
## <a name="syntax"></a>Синтаксис  
```  
cd <remotedirectory>  
```  
#### <a name="parameters"></a>Параметры  

|     Параметр     |                                 Описание                                 |
|-------------------|-----------------------------------------------------------------------------|
| <remotedirectory> | Указывает каталог на удаленном компьютере, который необходимо изменить. |

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Измените каталог на удаленном компьютере на **документы**.  
```  
cd Docs  
```  
Измените каталог на удаленном компьютере, чтобы он **мог получить видео**.  
```  
cd  May Videos  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
