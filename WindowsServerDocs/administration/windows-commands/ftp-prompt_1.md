---
title: prompt_1 FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 930df39b-45c4-4e0b-bfe2-1d1963be817a vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9d16f70226e91e2e845480be8d83481fd76af173
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843157"
---
# <a name="ftp-prompt_1"></a>FTP: prompt_1

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает и выключает режим **запроса** .   
## <a name="syntax"></a>Синтаксис  
```  
prompt  
```  
#### <a name="parameters"></a>Параметры  
нет  
## <a name="remarks"></a>Примечания  
- По умолчанию **запрос** включен.  
- запросы **FTP** при передаче нескольких файлов, позволяющие выборочно получать или хранить файлы.  **Mget** и **мпут** переносят все файлы, если **запрос** отключен.  
  ## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
  Включение и отключение режима подсказки.  
  ```  
  prompt  
  ```  
  ## <a name="additional-references"></a>Дополнительные материалы  
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
