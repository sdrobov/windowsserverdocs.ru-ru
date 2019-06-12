---
title: lpq
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb6abcc4-310a-4fa4-927b-4084b62ca02e vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 18ff1ff3ecbc2df0a437ec8a465dec9a12123ede
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66437509"
---
# <a name="lpq"></a>lpq

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает состояние очереди печати на компьютере под управлением Line printer Daemon (LPD).  

## <a name="syntax"></a>Синтаксис  
```  
lpq -S <ServerName> -P <printerName> [-l]  
```  
## <a name="parameters"></a>Параметры  

|    Параметр     |                                                                        Описание                                                                        |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| -S <ServerName>  | Указывает (по имени или IP-адрес) компьютера или общего доступа устройства, на котором размещается очередь печати LPD, с состоянием, которое будет отображаться. Обязательный. |
| -P <printerName> |                           Задает (по имени) принтера для очереди печати с состоянием, которое будет отображаться. Обязательный.                           |
|        -l        |                                      Указывает, что вы хотите отобразить сведения о состоянии очереди печати.                                      |
|        /?        |                                                           Отображение справки в командной строке.                                                            |

## <a name="remarks"></a>Примечания  
**-S** и **-P** параметры чувствительны к регистру и должны вводиться в верхнем регистре.  
## <a name="BKMK_examples"></a>Примеры  
В этом примере показано, как отобразить состояние очереди принтера Laserprinter1 на узле LPD на 10.0.0.45:  
```  
lpq -S 10.0.0.45 -P Laserprinter1  
```  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
[Описание команды печати](print-command-reference.md)  
