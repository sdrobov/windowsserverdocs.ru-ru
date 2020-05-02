---
title: prompt_1 FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 930df39b-45c4-4e0b-bfe2-1d1963be817a vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1abb697316a1072a9185a5132dfd22a1d8fd67dd
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725187"
---
# <a name="ftp-prompt_1"></a>FTP: prompt_1

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает и выключает режим **запроса** .   
## <a name="syntax"></a>Синтаксис  
```  
prompt  
```  
#### <a name="parameters"></a>Параметры  
none  
## <a name="remarks"></a>Примечания  
- По умолчанию **запрос** включен.  
- запросы **FTP** при передаче нескольких файлов, позволяющие выборочно получать или хранить файлы.  **Mget** и **мпут** переносят все файлы, если **запрос** отключен.  
  ## <a name="examples"></a>Примеры  
  Включение и отключение режима подсказки.  
  ```  
  prompt  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
