---
title: exit
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 23d1044b-f5c1-4180-ae6d-f553b48da4d9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 13cf7a7658394e59ce6cc7e66c3083cd3d359574
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844887"
---
# <a name="exit"></a>exit

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Выход из программы cmd. exe (интерпретатор команд) или текущего пакетного скрипта.  
В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.  
## <a name="syntax"></a>Синтаксис  
```  
exit [/b] [<exitCode>]  
```  
### <a name="parameters"></a>Параметры  

| Параметр  |                                                                                         Описание                                                                                          |
|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     /b     |                                      Выход из текущего пакетного скрипта вместо выхода из cmd. exe. Если выполняется из-за пределов пакетного скрипта, выполняет выход из cmd. exe.                                      |
| `<exitCode>` | Указывает числовое число. Если указан параметр **/b** , переменной среды ERRORLEVEL присваивается это число. При выходе из **cmd. exe**код завершения процесса устанавливается равным этому номеру. |
|     /?     |                                                                             Отображает справку в командной строке.                                                                             |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров  
Чтобы закрыть интерпретатор команд, cmd. exe введите:  
```  
exit  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  

