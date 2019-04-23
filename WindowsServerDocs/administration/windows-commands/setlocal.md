---
title: setlocal
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4e4b6d3-3f1a-4851-a782-25ee2470e16e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 70e58e3c3a7c3de594c620f7530816b57727d4c3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868865"
---
# <a name="setlocal"></a>setlocal



Запускает переменных среды в пакетном файле. Локализация продолжается, пока соответствующий **endlocal** команды или достигнут конец пакетного файла.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
setlocal [enableextensions | disableextensions] [enabledelayedexpansion | disabledelayedexpansion]
```

## <a name="arguments"></a>Аргументы

|Аргумент|Описание|
|--------|-----------|
|изменения|Включает расширения команд до соответствующего **endlocal** обнаружении команды, независимо от параметра до **setlocal** была выполнена команда.|
|DISABLEEXTENSIONS|Отключает расширения команд до соответствующего **endlocal** обнаружении команды, независимо от параметра до **setlocal** была выполнена команда.|
|enabledelayedexpansion|Включает расширение переменной среды с задержкой до соответствующего **endlocal** обнаружении команды, независимо от параметра до **setlocal** была выполнена команда.|
|disabledelayedexpansion|Отключает расширение переменной среды с задержкой до соответствующего **endlocal** обнаружении команды, независимо от параметра до **setlocal** была выполнена команда.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   С помощью **setlocal**

    При использовании **setlocal** за пределами файла скрипта или пакета, не влияет.
-   Изменение переменных среды

    Используйте **setlocal** для изменения переменных среды при выполнении пакетного файла. Изменения среды, выполненные после **setlocal** являются локальными для пакетного файла. Программа Cmd.exe восстанавливает предыдущие параметры, когда он встречает **endlocal** команды или достигнут конец пакетного файла.
-   Вложенность команды

    Можно иметь несколько **setlocal** или **endlocal** команды в пакетном файле (то есть вложенные команды).
-   Тестирование для расширения команд в пакетных файлах

    **Setlocal** команда задает переменной ERRORLEVEL. Если передать {**изменения** | **disableextensions**} или {**enabledelayedexpansion**  |   **disabledelayedexpansion**}, имеет значение переменной ERRORLEVEL **0** (ноль). В противном случае ему присваивается **1**. Эти сведения можно использовать в пакетных скриптах для определения расширения, доступны ли, как показано в следующем примере:  
    ```
    setlocal enableextensions
    verify other 2>nul
    if errorlevel 1 echo Unable to enable extensions
    ```  
    Так как **cmd** не задания переменной ERRORLEVEL, при отключении расширения команд **проверьте** команда инициализирует переменную ERRORLEVEL ненулевое значение, при использовании с недопустимым аргумент. Кроме того Если вы используете **setlocal** команды с аргументами {**изменения** | **disableextensions**} или {**enabledelayedexpansion**   |  **disabledelayedexpansion**} и для него не задано переменной ERRORLEVEL **1**, расширения команд не доступны.

## <a name="BKMK_examples"></a>Примеры

Вы можете локализовать переменные среды в пакетном файле, как показано в следующем примере скрипта:
```
rem *******Begin Comment**************
rem This program starts the superapp batch program on the network,
rem directs the output to a file, and displays the file
rem in Notepad.
rem *******End Comment**************
@echo off
setlocal
path=g:\programs\superapp;%path%
call superapp>c:\superapp.out
endlocal
start notepad c:\superapp.out
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)