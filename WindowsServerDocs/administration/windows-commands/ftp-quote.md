---
title: Квота FTP
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4500a1d3-c091-42c7-a909-f61df7f2e993 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0b1aaf9eadfd9c51048ad41106ce6532f6f9588b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59865885"
---
# <a name="ftp-quote"></a>FTP: Квота

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отправляет verbatim аргументы с удаленного FTP-сервером. Возвращается код ответа единый ftp.   
## <a name="syntax"></a>Синтаксис  
```  
quote <Argument>[ ]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<Argument>|Задает аргумент для отправки на сервер ftp.|  
## <a name="remarks"></a>Примечания  
**Квоты** команда идентична **литерала** команды.  
## <a name="BKMK_Examples"></a>Примеры  
Отправить **выйти из программы** команду на удаленном FTP-сервер.  
```  
quote quit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [ftp: literal_1](ftp-literal_1.md)  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
