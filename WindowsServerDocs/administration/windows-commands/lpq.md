---
title: lpq
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 6a3755c010c9bb4549deed08f26b5a0670fe7318
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374202"
---
# <a name="lpq"></a>lpq

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает состояние очереди печати на компьютере, на котором запущена управляющая программа LPR.  

## <a name="syntax"></a>Синтаксис  
```  
lpq -S <ServerName> -P <printerName> [-l]  
```  
## <a name="parameters"></a>Параметры  

|    Параметр     |                                                                        Описание                                                                        |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| -S <ServerName>  | Указывает (по имени или IP-адресу) устройство общего доступа к компьютеру или принтеру, на котором размещена очередь печати LPD, с состоянием, которое необходимо отобразить. Обязательный. |
| -P <printerName> |                           Указывает (по имени) принтер для очереди печати с состоянием, которое необходимо отобразить. Обязательный.                           |
|        -l        |                                      Указывает, что необходимо отобразить сведения о состоянии очереди печати.                                      |
|        /?        |                                                           Отображение справки в командной строке.                                                            |

## <a name="remarks"></a>Примечания  
Параметры **-S** и **-P** чувствительны к регистру и должны вводиться в верхнем регистре.  
## <a name="BKMK_examples"></a>Примеров  
В этом примере показано, как отобразить состояние очереди принтера Laserprinter1 на узле LPD в 10.0.0.45:  
```  
lpq -S 10.0.0.45 -P Laserprinter1  
```  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
[Справочник по командам печати](print-command-reference.md)  
