---
title: remotehelp_1 FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ef23adf3-ead4-44c8-ac1d-c8a6f4b2bf73 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dc4affb3f04eadaa4e0005e5edce0f564156f64a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725133"
---
# <a name="ftp-remotehelp_1"></a>FTP: remotehelp_1

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает справку по удаленным командам.   
## <a name="syntax"></a>Синтаксис  
```  
remotehelp [<Command>]  
```  
#### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|[<Command>]|Указывает имя команды, для которой требуется справка. Если *команда* не указана, **протокол FTP** отображает список всех удаленных команд.|  
## <a name="remarks"></a>Примечания  
Удаленные команды можно выполнять с помощью **кавычек** или **Literal**.  
## <a name="examples"></a>Примеры  
Отображение списка удаленных команд.  
```  
remotehelp  
```  
Отображение синтаксиса для удаленной команды **достижением** .  
```  
remotehelp feat  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: кавычка](ftp-quote.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
