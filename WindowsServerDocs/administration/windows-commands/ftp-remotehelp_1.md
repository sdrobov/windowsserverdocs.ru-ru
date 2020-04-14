---
title: remotehelp_1 FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ef23adf3-ead4-44c8-ac1d-c8a6f4b2bf73 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3c4a4ffec01fce5cde8b2aa9dd1fa0704f3a85ff
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843057"
---
# <a name="ftp-remotehelp_1"></a>FTP: remotehelp_1

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Отображение списка удаленных команд.  
```  
remotehelp  
```  
Отображение синтаксиса для удаленной команды **достижением** .  
```  
remotehelp feat  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   [FTP: кавычка](ftp-quote.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
