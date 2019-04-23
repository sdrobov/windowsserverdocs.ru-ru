---
title: FTP literal_1
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fb81aa2d-07fa-4e79-bf44-1fb5526fdf14 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d50c6356dfa56a4a1c22c09b08dffc6b3a514c4a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879265"
---
# <a name="ftp-literal1"></a>ftp: literal_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 отправляет verbatim аргументы с удаленного FTP-сервером. Возвращается код ответа единый ftp.   

## <a name="syntax"></a>Синтаксис  
```  
literal <Argument> [ ]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<Argument>|Задает аргумент для отправки на сервер ftp.|  
## <a name="remarks"></a>Примечания  
**Литерала** команда идентична **квоты** команды.  
## <a name="BKMK_Examples"></a>Примеры  
Отправить **выйти из программы** команду на удаленном FTP-сервер.  
```  
literal quit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: Квота](ftp-quote.md)  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
