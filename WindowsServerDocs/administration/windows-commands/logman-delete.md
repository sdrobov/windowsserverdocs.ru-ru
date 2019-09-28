---
title: logman delete
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f3b2422-3dce-4fb4-adbb-8536b1d7da2b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8360a4955a5ebed3eb25fda77acf587c56fbf5d6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374434"
---
# <a name="logman-delete"></a>logman delete

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаление существующего сборщика данных.  

## <a name="syntax"></a>Синтаксис  
```  
logman delete <[-n] <name>> [options]  
```  
## <a name="parameters"></a>Параметры  

|        Параметр        |                                                                               Описание                                                                               |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           /?            |                                                                    Отображает контекстную справку.                                                                     |
|   -s <computer name>    |                                                          Выполните команду на указанном удаленном компьютере.                                                          |
|     -config <value>     |                                                         Указывает файл параметров, содержащий параметры команды.                                                         |
|       [-n] <name>       |                                                                   Имя целевого сборщика данных.                                                                    |
|          -ETS           |                                              Отправка команд в сеансы трассировки событий напрямую без сохранения или планирования.                                               |
| -[-] u < пользователь [пароль] > | Указывает пользователя для запуска от имени. При вводе \* для пароля выводится запрос на ввод пароля. Пароль не отображается при вводе пароля в командной строке. |

## <a name="BKMK_examples"></a>Примеров  
Следующая команда удаляет perf_log сборщика данных.  
```  
logman delete perf_log  
```  
#### <a name="additional-references"></a>Дополнительные ссылки  
[logman](logman.md)  
