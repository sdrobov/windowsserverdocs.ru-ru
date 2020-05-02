---
title: ntcmdprompt
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0063bdbb-dc2b-41c4-99ee-b011603aaa86
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b5b0dcbc0735f20b63cbf441f4014411acd3a48e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723474"
---
# <a name="ntcmdprompt"></a>ntcmdprompt

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запускает интерпретатор команд **cmd. exe**, а не **Command.com**, после выполнения команды завершить и оставаться резидентным (резидентным программным обеспечением) или после запуска командной строки в приложении MS-DOS.
## <a name="syntax"></a>Синтаксис
```
ntcmdprompt
```
#### <a name="parameters"></a>Параметры

| Параметр |             Описание              |
|-----------|--------------------------------------|
|    /?     | Отображение справки в командной строке. |

## <a name="remarks"></a>Примечания
- Когда **Command.com** работает, некоторые функции **cmd. exe**, например, вывод журнала команд **Doskey** , недоступны. Если вы предпочитаете запустить интерпретатор команд **cmd. exe** после начала и сохранения резидентных (резидентных) приложений или запуска командную строку из приложения на основе MS-DOS, можно использовать команду **нткмдпромпт** . Однако помните, что РЕЗИДЕНТная программа может быть недоступна для использования при запуске **cmd. exe**. Команду **нткмдпромпт** можно включить в файл **config. NT** или в эквивалентный пользовательский файл запуска в файле сведений о программе (PIF) приложения.
  ## <a name="examples"></a>Примеры
  Чтобы включить **нткмдпромпт** в файл **config. NT** или файл запуска конфигурации, указанный в PIF, введите: **нткмдпромпт** .
  ## <a name="additional-references"></a>Дополнительные ссылки
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

