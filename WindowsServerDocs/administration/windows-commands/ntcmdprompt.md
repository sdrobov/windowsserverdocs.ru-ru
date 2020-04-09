---
title: ntcmdprompt
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0063bdbb-dc2b-41c4-99ee-b011603aaa86
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 25afab00ced3cb14771c18aa38c7fd8c98aecc0c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838047"
---
# <a name="ntcmdprompt"></a>ntcmdprompt

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запускает интерпретатор команд **cmd. exe**, а не **Command.com**, после выполнения команды завершить и оставаться резидентным (резидентным программным обеспечением) или после запуска командной строки в приложении MS-DOS.
## <a name="syntax"></a>Синтаксис
```
ntcmdprompt
```
#### <a name="parameters"></a>Параметры

| Параметр |             Описание              |
|-----------|--------------------------------------|
|    /?     | Отображает справку в командной строке. |

## <a name="remarks"></a>Примечания
- Когда **Command.com** работает, некоторые функции **cmd. exe**, например, вывод журнала команд **Doskey** , недоступны. Если вы предпочитаете запустить интерпретатор команд **cmd. exe** после начала и сохранения резидентных (резидентных) приложений или запуска командную строку из приложения на основе MS-DOS, можно использовать команду **нткмдпромпт** . Однако помните, что РЕЗИДЕНТная программа может быть недоступна для использования при запуске **cmd. exe**. Команду **нткмдпромпт** можно включить в файл **config. NT** или в эквивалентный пользовательский файл запуска в файле сведений о программе (PIF) приложения.
  ## <a name="examples"></a>Примеры
  Чтобы включить **нткмдпромпт** в файл **config. NT** или файл запуска конфигурации, указанный в PIF, введите: **нткмдпромпт** .
  ## <a name="additional-references"></a>Дополнительные материалы
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

