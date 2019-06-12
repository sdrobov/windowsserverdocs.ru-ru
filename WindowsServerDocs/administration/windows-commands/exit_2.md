---
title: выход
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23d1044b-f5c1-4180-ae6d-f553b48da4d9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4e599f84389b23e527e3718a620d5fdfefe24edb
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66439459"
---
# <a name="exit"></a>выход

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Выполняет выход из программы Cmd.exe (интерпретатор команд) или текущего пакетного сценария.  
Примеры для использования этой команды, см. в разделе [примеры](#BKMK_examples).  
## <a name="syntax"></a>Синтаксис  
```  
exit [/b] [<exitCode>]  
```  
## <a name="parameters"></a>Параметры  

| Параметр  |                                                                                         Описание                                                                                          |
|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     /b     |                                      Выполняет выход из текущего пакетного сценария вместо завершения работы Cmd.exe. Если выполняется вне пакетного скрипта, выхода из Cmd.exe.                                      |
| <exitCode> | Указывает числовое значение. Если **/b** указан, этот номер имеет значение переменной среды ERRORLEVEL. Если вы выход из приложения **Cmd.exe**, код завершения процесса имеет значение этого числа. |
|     /?     |                                                                             Отображение справки в командной строке.                                                                             |

## <a name="BKMK_examples"></a>Примеры  
Чтобы закрыть интерпретатор команд Cmd.exe, введите следующую команду:  
```  
exit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  

