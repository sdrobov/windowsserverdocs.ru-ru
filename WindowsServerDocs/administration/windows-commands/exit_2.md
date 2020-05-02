---
title: exit
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 23d1044b-f5c1-4180-ae6d-f553b48da4d9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e47dfa42f2bacb3fe9f12d1da9163bcf828e9488
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725706"
---
# <a name="exit"></a>exit

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Выход из программы cmd. exe (интерпретатор команд) или текущего пакетного скрипта.  
  
## <a name="syntax"></a>Синтаксис  
```  
exit [/b] [<exitCode>]  
```  
### <a name="parameters"></a>Параметры  

| Параметр  |                                                                                         Описание                                                                                          |
|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     /b     |                                      Выход из текущего пакетного скрипта вместо выхода из cmd. exe. Если выполняется из-за пределов пакетного скрипта, выполняет выход из cmd. exe.                                      |
| `<exitCode>` | Указывает числовое число. Если указан параметр **/b** , переменной среды ERRORLEVEL присваивается это число. При выходе из **cmd. exe**код завершения процесса устанавливается равным этому номеру. |
|     /?     |                                                                             Отображение справки в командной строке.                                                                             |

## <a name="examples"></a>Примеры  
Чтобы закрыть интерпретатор команд, cmd. exe введите:  
```  
exit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  

