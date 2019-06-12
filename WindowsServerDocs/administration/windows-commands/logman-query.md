---
title: logman query
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1116a0f0-5415-4369-a045-12f79f8f66de
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6e00e1ca7e6e090fd618af5b0ca2307bb573ab8c
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66437719"
---
# <a name="logman-query"></a>logman query

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

сборщик данных запросов или сборщика данных свойства.  

## <a name="syntax"></a>Синтаксис  
```  
logman query [providers|"Data Collector Set name"] [options]  
```  
## <a name="parameters"></a>Параметры  

|     Параметр      |                                 Описание                                  |
|--------------------|------------------------------------------------------------------------------|
|         /?         |                       Отображение контекстной справки.                       |
| -s <computer name> |            Выполнение команды на удаленный компьютер.             |
|  -config <value>   |           Указывает файл параметров, содержащий параметры команды.            |
|    [-n]. <name>     |                          Имя целевого объекта.                          |
|        -ets        | Отправьте команды сеансам трассировки событий напрямую без сохранения или планирования. |

## <a name="BKMK_examples"></a>Примеры  
Следующая команда перечисляет все наборы сборщиков данных, настроенный на целевой системе.  
```  
logman query  
```  
Следующая команда перечисляет сборщиков данных, содержащихся в сборщиков данных, с именем perf_log.  
```  
logman query "perf_log"  
```  
Следующая команда перечисляет все доступные поставщики сборщиков данных в целевой системе.  
```  
logman query providers  
```  
#### <a name="additional-references"></a>Дополнительные ссылки  
[logman](logman.md)  
