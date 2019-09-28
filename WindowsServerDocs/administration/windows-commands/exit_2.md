---
title: выход
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23d1044b-f5c1-4180-ae6d-f553b48da4d9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 105bf572c1ebeb37ea59ff8bc5c04121d2442341
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377346"
---
# <a name="exit"></a>выход

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

выход из программы cmd. exe (интерпретатор команд) или текущего пакетного скрипта.  
Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).  
## <a name="syntax"></a>Синтаксис  
```  
exit [/b] [<exitCode>]  
```  
## <a name="parameters"></a>Параметры  

| Параметр  |                                                                                         Описание                                                                                          |
|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     b     |                                      выход из текущего пакетного скрипта вместо выхода из cmd. exe. Если выполняется из-за пределов пакетного скрипта, выполняет выход из cmd. exe.                                      |
| <exitCode> | Указывает числовое число. Если указан параметр **/b** , переменной среды ERRORLEVEL присваивается это число. При выходе из **cmd. exe**код завершения процесса устанавливается равным этому номеру. |
|     /?     |                                                                             Отображение справки в командной строке.                                                                             |

## <a name="BKMK_examples"></a>Примеров  
Чтобы закрыть интерпретатор команд, cmd. exe введите:  
```  
exit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  

