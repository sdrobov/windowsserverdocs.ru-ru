---
title: FTP prompt_1
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 65f7505dfcb3677fcaace9bd645cca7e7ba70b7d
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438591"
---
# <a name="ftp-prompt1"></a>ftp: prompt_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Переключение между **строке** режима включения и отключения.   
## <a name="syntax"></a>Синтаксис  
```  
prompt  
```  
### <a name="parameters"></a>Параметры  
none  
## <a name="remarks"></a>Примечания  
- По умолчанию **строке** включен.  
- **FTP** запрашивает при передаче нескольких файлов, чтобы можно было выборочно получить или сохранить файлы.  **Mget** и **mput** передавать все файлы в том случае, если **строке** отключен.  
  ## <a name="BKMK_Examples"></a>Примеры  
  Включить режим подсказки и отключить.  
  ```  
  prompt  
  ```  
  ## <a name="additional-references"></a>Дополнительные ссылки  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
