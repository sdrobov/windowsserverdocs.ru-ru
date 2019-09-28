---
title: logman query
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 6acf6cf5240dd59357f4c788577190699a354744
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374418"
---
# <a name="logman-query"></a>logman query

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

запросите свойства группы сборщиков данных или сбора данных.  

## <a name="syntax"></a>Синтаксис  
```  
logman query [providers|"Data Collector Set name"] [options]  
```  
## <a name="parameters"></a>Параметры  

|     Параметр      |                                 Описание                                  |
|--------------------|------------------------------------------------------------------------------|
|         /?         |                       Отображает контекстную справку.                       |
| -s <computer name> |            Выполните команду на указанном удаленном компьютере.             |
|  -config <value>   |           Указывает файл параметров, содержащий параметры команды.            |
|    [-n] <name>     |                          Имя целевого объекта.                          |
|        -ETS        | Отправка команд в сеансы трассировки событий напрямую без сохранения или планирования. |

## <a name="BKMK_examples"></a>Примеров  
Следующая команда выводит список всех наборов сборщиков данных, настроенных в целевой системе.  
```  
logman query  
```  
Следующая команда перечисляет сборщики данных, содержащиеся в наборе сборщиков данных с именем perf_log.  
```  
logman query "perf_log"  
```  
Следующая команда выводит список всех доступных поставщиков сборщиков данных в целевой системе.  
```  
logman query providers  
```  
#### <a name="additional-references"></a>Дополнительные ссылки  
[logman](logman.md)  
