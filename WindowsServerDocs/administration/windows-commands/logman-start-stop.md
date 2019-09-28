---
title: Запуск Logman | позиции
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a40006a1-876e-474b-aaf1-f365c730deea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 395d325b31ee596e1394e7ed796a444f159d15fc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374407"
---
# <a name="logman-start--stop"></a>Запуск Logman | позиции

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

запустите сборщик данных и задайте время начала вручную или закройте группу сборщиков данных и задайте для параметра время окончания значение вручную.  

## <a name="syntax"></a>Синтаксис  
```  
logman start <[-n] <name>> [options]  
logman stop <[-n] <name>> [options]  
```  
## <a name="parameters"></a>Параметры  

|     Параметр      |                                 Описание                                  |
|--------------------|------------------------------------------------------------------------------|
|         -?         |                       Отображает контекстную справку.                       |
| -s <computer name> |            Выполните команду на указанном удаленном компьютере.             |
|  -config <value>   |           Указывает файл параметров, содержащий параметры команды.            |
|    [-n] <name>     |                          Имя целевого объекта.                          |
|        -ETS        | Отправка команд в сеансы трассировки событий напрямую без сохранения или планирования. |
|        — как         |               Выполнение запрошенной операции в асинхронном режиме.                |

## <a name="BKMK_examples"></a>Примеров  
Следующая команда запускает сборщик данных perf_log на удаленном компьютере server_1.  
```  
logman start perf_log -s server_1  
```  
#### <a name="additional-references"></a>Дополнительные ссылки  
[logman](logman.md)  
