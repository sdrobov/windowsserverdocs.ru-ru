---
title: Logman import | Экспорт
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c258daba-fb93-47c0-a53b-2fe83ed2c743
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2d68f5f340476bbb783c47f9c3fe9c060105b4e4
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66437713"
---
# <a name="logman-import--export"></a>Logman import | Экспорт

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

импортировать группу сборщиков данных из XML-файла или экспортировать сборщиков данных в XML-файл.  

## <a name="syntax"></a>Синтаксис  
```  
logman import <[-n] <name>> <-xml <name>> [options]  
logman export <[-n] <name>> <-xml <name>> [options]  
```  
## <a name="parameters"></a>Параметры  

|        Параметр        |                                                                        Описание                                                                        |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
|           -?            |                                                             Отображение контекстной справки.                                                              |
|   -s <computer name>    |                                                   Выполнение команды на удаленный компьютер.                                                   |
|     -config <value>     |                                                  Указывает файл параметров, содержащий параметры команды.                                                  |
|       [-n]. <name>       |                                                                Имя целевого объекта.                                                                 |
|       -xml <name>       |                                                         Имя XML-файла для импорта или экспорта.                                                         |
|          -ets           |                                       Отправьте команды сеансам трассировки событий напрямую без сохранения или планирования.                                        |
| -[-]u <user [password]> | Пользователь, запуск от имени. Введя \* для пароля выводит приглашение для ввода пароля. Пароль не отображается при вводе пароля. |
|           -y            |                                                      Да, ответьте на все вопросы без запроса подтверждения.                                                       |

## <a name="BKMK_examples"></a>Примеры  
Следующая команда импортирует c:\windows\perf_log.xml файл XML из server_1 компьютера, как группы сборщиков данных вызываемой perf_log.  
```  
logman import perf_log -s server_1 -xml "c:\windows\perf_log.xml"  
```  
#### <a name="additional-references"></a>Дополнительные ссылки  
[logman](logman.md)  
