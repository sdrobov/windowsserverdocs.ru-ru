---
title: FTP ЖК-экрана
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 60a25808-6abb-408b-8373-0bbdcd0994b4 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: eac028c8aa675e680dedefcfe9f0b8da18ce7179
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59826895"
---
# <a name="ftp-lcd"></a>FTP: ЖК-экрана

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет рабочий каталог на локальном компьютере. По умолчанию, рабочий каталог — это каталог, в котором **ftp** был запущен.   
## <a name="syntax"></a>Синтаксис  
```  
lcd [<directory>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|[<directory>]|Указывает каталог на локальном компьютере, для которого изменяется. Если *directory* не указан, текущий рабочий каталог изменяется в каталог по умолчанию.|  
## <a name="BKMK_Examples"></a>Примеры  
Измените рабочую папку на локальном компьютере для **C:\dir1**  
```  
lcd C:\dir1  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
