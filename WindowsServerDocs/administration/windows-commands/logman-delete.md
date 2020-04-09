---
title: logman delete
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8f3b2422-3dce-4fb4-adbb-8536b1d7da2b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e0ab38eab988770de4fbcef8af2c7be6a6137b16
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80840757"
---
# <a name="logman-delete"></a>logman delete

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаление существующего сборщика данных.  

## <a name="syntax"></a>Синтаксис  
```  
logman delete <[-n] <name>> [options]  
```  
### <a name="parameters"></a>Параметры  

|        Параметр        |                                                                               Описание                                                                               |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           /?            |                                                                    Отображает контекстную справку.                                                                     |
|   -s <computer name>    |                                                          Выполните команду на указанном удаленном компьютере.                                                          |
|     -config <value>     |                                                         Указывает файл параметров, содержащий параметры команды.                                                         |
|       [-n] <name>       |                                                                   Имя целевого сборщика данных.                                                                    |
|          -ETS           |                                              Отправка команд в сеансы трассировки событий напрямую без сохранения или планирования.                                               |
| -[-] u < пользователь [пароль] > | Указывает пользователя для запуска от имени. При вводе \* пароля выводится запрос на ввод пароля. Пароль не отображается при вводе пароля в командной строке. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров  
Следующая команда удаляет perf_log сборщика данных.  
```  
logman delete perf_log  
```  
## <a name="additional-references"></a>Дополнительные материалы  
[logman](logman.md)  
