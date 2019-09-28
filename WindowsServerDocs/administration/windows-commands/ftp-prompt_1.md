---
title: prompt_1 FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 930df39b-45c4-4e0b-bfe2-1d1963be817a vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 08c7f9c14f4168bb5d3aa874711669eede8d0d87
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376197"
---
# <a name="ftp-prompt_1"></a>FTP: prompt_1

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает и выключает режим **запроса** .   
## <a name="syntax"></a>Синтаксис  
```  
prompt  
```  
### <a name="parameters"></a>Параметры  
none  
## <a name="remarks"></a>Примечания  
- По умолчанию **запрос** включен.  
- запросы **FTP** при передаче нескольких файлов, позволяющие выборочно получать или хранить файлы.  **Mget** и **мпут** переносят все файлы, если **запрос** отключен.  
  ## <a name="BKMK_Examples"></a>Примеров  
  Включение и отключение режима подсказки.  
  ```  
  prompt  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
