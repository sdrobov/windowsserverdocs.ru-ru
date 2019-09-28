---
title: ntcmdprompt
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 5fef1641bf1b48bd1fe4aaf284ed309ab4d4d5f1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372667"
---
# <a name="ntcmdprompt"></a>ntcmdprompt

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запускает интерпретатор команд **cmd. exe**, а не **Command.com**, после выполнения команды завершить и оставаться резидентным (резидентным программным обеспечением) или после запуска командной строки в приложении MS-DOS.
## <a name="syntax"></a>Синтаксис
```
ntcmdprompt
```
### <a name="parameters"></a>Параметры

| Параметр |             Описание              |
|-----------|--------------------------------------|
|    /?     | Отображение справки в командной строке. |

## <a name="remarks"></a>Примечания
- Когда **Command.com** работает, некоторые функции **cmd. exe**, например, вывод журнала команд **Doskey** , недоступны. Если вы предпочитаете запустить интерпретатор команд **cmd. exe** после начала и сохранения резидентных (резидентных) приложений или запуска командную строку из приложения на основе MS-DOS, можно использовать команду **нткмдпромпт** . Однако помните, что РЕЗИДЕНТная программа может быть недоступна для использования при запуске **cmd. exe**. Команду **нткмдпромпт** можно включить в файл **config. NT** или в эквивалентный пользовательский файл запуска в файле сведений о программе (PIF) приложения.
  ## <a name="examples"></a>Примеры
  Чтобы включить **нткмдпромпт** в файл **config. NT** или файл запуска конфигурации, указанный в PIF, введите: **нткмдпромпт** .
  ## <a name="additional-references"></a>Дополнительные ссылки
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

