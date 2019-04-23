---
title: FTP remotehelp_1
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef23adf3-ead4-44c8-ac1d-c8a6f4b2bf73 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bd64af157f7ce05330cdafe6e4db6787fa765859
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889595"
---
# <a name="ftp-remotehelp1"></a>FTP: remotehelp_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает справку для удаленных команд.   
## <a name="syntax"></a>Синтаксис  
```  
remotehelp [<Command>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|[<Command>]|Задает имя команды, о которой требуется справка. Если *команда* не указан, **ftp** отображает список всех удаленных команд.|  
## <a name="remarks"></a>Примечания  
Можно запустить с помощью удаленных команд **квоты** или **литерала**.  
## <a name="BKMK_Examples"></a>Примеры  
Отображение списка удаленных команд.  
```  
remotehelp  
```  
Отображают сведения о синтаксисе для **проделывать** удаленной команды.  
```  
remotehelp feat  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: Квота](ftp-quote.md)  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
