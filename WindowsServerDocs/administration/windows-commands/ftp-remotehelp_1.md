---
title: remotehelp_1 FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: bac6fbe4a55c3fed4caab4e30ba848ec9ea68e21
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376029"
---
# <a name="ftp-remotehelp_1"></a>FTP: remotehelp_1

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает справку по удаленным командам.   
## <a name="syntax"></a>Синтаксис  
```  
remotehelp [<Command>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|[<Command>]|Указывает имя команды, для которой требуется справка. Если *команда* не указана, **протокол FTP** отображает список всех удаленных команд.|  
## <a name="remarks"></a>Примечания  
Удаленные команды можно выполнять с помощью **кавычек** или **Literal**.  
## <a name="BKMK_Examples"></a>Примеров  
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
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
