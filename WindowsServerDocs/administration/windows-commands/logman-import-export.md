---
title: Logman Import | программе
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c258daba-fb93-47c0-a53b-2fe83ed2c743
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ffc2e42f353352f69cf61dfb1f108a7d53cb7c4b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724363"
---
# <a name="logman-import--export"></a>Logman Import | программе

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Импорт набора сборщиков данных из XML-файла или экспорт набора сборщиков данных в XML-файл.  

## <a name="syntax"></a>Синтаксис  
```  
logman import <[-n] <name>> <-xml <name>> [options]  
logman export <[-n] <name>> <-xml <name>> [options]  
```  
### <a name="parameters"></a>Параметры  

|        Параметр        |                                                                        Описание                                                                        |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
|           -?            |                                                             Отображает контекстную справку.                                                              |
|   -s<computer name>    |                                                   Выполните команду на указанном удаленном компьютере.                                                   |
|     -config <value>     |                                                  Указывает файл параметров, содержащий параметры команды.                                                  |
|       [-n]<name>       |                                                                Имя целевого объекта.                                                                 |
|       -XML<name>       |                                                         Имя XML-файла для импорта или экспорта.                                                         |
|          -ETS           |                                       Отправка команд в сеансы трассировки событий напрямую без сохранения или планирования.                                        |
| -[-] u <пользователь [пароль] > | Пользователь для запуска от имени. \* При вводе для пароля выводится запрос на ввод пароля. Пароль не отображается при вводе пароля в командной строке. |
|           -y            |                                                      Ответьте Да на все вопросы без запроса.                                                       |

## <a name="examples"></a>Примеры  
Следующая команда импортирует XML-файл к:\виндовс\ perf_log. XML с компьютера server_1 как набор сборщиков данных с именем perf_log.  
```  
logman import perf_log -s server_1 -xml c:\windows\perf_log.xml  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
[logman](logman.md)  
