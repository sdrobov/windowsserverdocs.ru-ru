---
title: ntcmdprompt
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0063bdbb-dc2b-41c4-99ee-b011603aaa86
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 65804f99095d0c0a56537b1d155ac26e768f61a7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59827665"
---
# <a name="ntcmdprompt"></a>ntcmdprompt

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запускает интерпретатор команд **Cmd.exe**, а не **Command.com**, после выполнения завершения и оставаться резидентном Резидентная, или после запуска командную строку из приложения MS-DOS.
## <a name="syntax"></a>Синтаксис
```
ntcmdprompt
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/?|Отображение справки в командной строке.|
## <a name="remarks"></a>Примечания
-   Когда **Command.com** работает, некоторые возможности **Cmd.exe**, такие как **doskey** отображение журнала команд, которые недоступны. Если вы хотите использовать для запуска **Cmd.exe** интерпретатор команд после вы Terminate и оставаться резидентном Резидентная или командную строку из приложения MS-DOS, можно использовать **ntcmdprompt**  команды. Однако следует помнить, что Резидентная недоступен для использования при запуске **Cmd.exe**. Можно включить **ntcmdprompt** в команду вашей **Config.nt** файл или файл эквивалентный командный файл приложения (Pif).
## <a name="examples"></a>Примеры
Чтобы включить **ntcmdprompt** в вашей **Config.nt** файл или файл конфигурации запуска, заданный в файле Pif, тип: **ntcmdprompt**
## <a name="additional-references"></a>Дополнительные ссылки
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)

