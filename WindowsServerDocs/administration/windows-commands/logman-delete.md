---
title: logman delete
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8f3b2422-3dce-4fb4-adbb-8536b1d7da2b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8b30fd6eb7915d3d0296988a98968dcde58bdbc2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724377"
---
# <a name="logman-delete"></a>logman delete

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаление существующего сборщика данных.  

## <a name="syntax"></a>Синтаксис  
```  
logman delete <[-n] <name>> [options]  
```  
### <a name="parameters"></a>Параметры  

|        Параметр        |                                                                               Описание                                                                               |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           /?            |                                                                    Отображает контекстную справку.                                                                     |
|   -s<computer name>    |                                                          Выполните команду на указанном удаленном компьютере.                                                          |
|     -config <value>     |                                                         Указывает файл параметров, содержащий параметры команды.                                                         |
|       [-n]<name>       |                                                                   Имя целевого сборщика данных.                                                                    |
|          -ETS           |                                              Отправка команд в сеансы трассировки событий напрямую без сохранения или планирования.                                               |
| -[-] u <пользователь [пароль] > | Указывает пользователя для запуска от имени. \* При вводе для пароля выводится запрос на ввод пароля. Пароль не отображается при вводе пароля в командной строке. |

## <a name="examples"></a>Примеры  
Следующая команда удаляет perf_log сборщика данных.  
```  
logman delete perf_log  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
[logman](logman.md)  
