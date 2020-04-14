---
title: ЖК-монитор FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 60a25808-6abb-408b-8373-0bbdcd0994b4 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0d7e2e6fc9f6af7655381bfb802dc190e79365bd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843407"
---
# <a name="ftp-lcd"></a>FTP: ЖК

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет рабочий каталог на локальном компьютере. По умолчанию рабочий каталог — это каталог, в котором был запущен **FTP** .   
## <a name="syntax"></a>Синтаксис  
```  
lcd [<directory>]  
```  
#### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|[<directory>]|Указывает каталог на локальном компьютере, который необходимо изменить. Если *Каталог* не указан, текущий рабочий каталог изменяется на каталог по умолчанию.|  
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
изменение рабочего каталога на локальном компьютере до **C:\Dir1**  
```  
lcd C:\dir1  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
