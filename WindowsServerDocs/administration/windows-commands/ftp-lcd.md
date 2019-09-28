---
title: ЖК-монитор FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 47058cc62e4e87d1fcd951ec3b4a7885eeef2ae2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376307"
---
# <a name="ftp-lcd"></a>FTP: ЖК

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет рабочий каталог на локальном компьютере. По умолчанию рабочий каталог — это каталог, в котором был запущен **FTP** .   
## <a name="syntax"></a>Синтаксис  
```  
lcd [<directory>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|[<directory>]|Указывает каталог на локальном компьютере, который необходимо изменить. Если *Каталог* не указан, текущий рабочий каталог изменяется на каталог по умолчанию.|  
## <a name="BKMK_Examples"></a>Примеров  
изменение рабочего каталога на локальном компьютере до **C:\Dir1**  
```  
lcd C:\dir1  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
