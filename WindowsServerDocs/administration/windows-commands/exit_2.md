---
title: выход
description: 'Раздел команд Windows для * * * *- '
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
ms.openlocfilehash: d6d3a4d0bfc74644f6fda43abe57e0e4e7c1264a
ms.sourcegitcommit: 4a03f263952c993dfdf339dd3491c73719854aba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74791227"
---
# <a name="exit"></a>выход

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Выход из программы cmd. exe (интерпретатор команд) или текущего пакетного скрипта.  
В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.  
## <a name="syntax"></a>Синтаксис  
```  
exit [/b] [<exitCode>]  
```  
## <a name="parameters"></a>Параметры  

| Параметр  |                                                                                         Описание                                                                                          |
|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     b     |                                      Выход из текущего пакетного скрипта вместо выхода из cmd. exe. Если выполняется из-за пределов пакетного скрипта, выполняет выход из cmd. exe.                                      |
| `<exitCode>` | Указывает числовое число. Если указан параметр **/b** , переменной среды ERRORLEVEL присваивается это число. При выходе из **cmd. exe**код завершения процесса устанавливается равным этому номеру. |
|     /?     |                                                                             Отображение справки в командной строке.                                                                             |

## <a name="BKMK_examples"></a>Примеров  
Чтобы закрыть интерпретатор команд, cmd. exe введите:  
```  
exit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  

