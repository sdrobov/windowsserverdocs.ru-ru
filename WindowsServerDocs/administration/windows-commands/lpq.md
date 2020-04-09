---
title: lpq
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bb6abcc4-310a-4fa4-927b-4084b62ca02e vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 051b1983fcc0fddd7b69e561c0a27a120f78d998
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80840397"
---
# <a name="lpq"></a>lpq

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает состояние очереди печати на компьютере, на котором запущена управляющая программа LPR.  

## <a name="syntax"></a>Синтаксис  
```  
lpq -S <ServerName> -P <printerName> [-l]  
```  
### <a name="parameters"></a>Параметры  

|    Параметр     |                                                                        Описание                                                                        |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| -S <ServerName>  | Указывает (по имени или IP-адресу) устройство общего доступа к компьютеру или принтеру, на котором размещена очередь печати LPD, с состоянием, которое необходимо отобразить. Обязательное. |
| -P <printerName> |                           Указывает (по имени) принтер для очереди печати с состоянием, которое необходимо отобразить. Обязательное.                           |
|        -l        |                                      Указывает, что необходимо отобразить сведения о состоянии очереди печати.                                      |
|        /?        |                                                           Отображает справку в командной строке.                                                            |

## <a name="remarks"></a>Примечания  
Параметры **-S** и **-P** чувствительны к регистру и должны вводиться в верхнем регистре.  
## <a name="examples"></a><a name=BKMK_examples></a>Примеров  
В этом примере показано, как отобразить состояние очереди принтера Laserprinter1 на узле LPD в 10.0.0.45:  
```  
lpq -S 10.0.0.45 -P Laserprinter1  
```  
## <a name="additional-references"></a>Дополнительные материалы  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
[Справочник по командам печати](print-command-reference.md)  
