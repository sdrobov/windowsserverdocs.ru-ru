---
title: Запуск Logman | позиции
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a40006a1-876e-474b-aaf1-f365c730deea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2bd81a33779aa58e7528d0173a7a4b49489de8f9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80840627"
---
# <a name="logman-start--stop"></a>Запуск Logman | позиции

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

запустите сборщик данных и задайте время начала вручную или закройте группу сборщиков данных и задайте для параметра время окончания значение вручную.  

## <a name="syntax"></a>Синтаксис  
```  
logman start <[-n] <name>> [options]  
logman stop <[-n] <name>> [options]  
```  
### <a name="parameters"></a>Параметры  

|     Параметр      |                                 Описание                                  |
|--------------------|------------------------------------------------------------------------------|
|         -?         |                       Отображает контекстную справку.                       |
| -s <computer name> |            Выполните команду на указанном удаленном компьютере.             |
|  -config <value>   |           Указывает файл параметров, содержащий параметры команды.            |
|    [-n] <name>     |                          Имя целевого объекта.                          |
|        -ETS        | Отправка команд в сеансы трассировки событий напрямую без сохранения или планирования. |
|        — как         |               Выполнение запрошенной операции в асинхронном режиме.                |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров  
Следующая команда запускает сборщик данных perf_log на удаленном компьютере server_1.  
```  
logman start perf_log -s server_1  
```  
## <a name="additional-references"></a>Дополнительные материалы  
[logman](logman.md)  
