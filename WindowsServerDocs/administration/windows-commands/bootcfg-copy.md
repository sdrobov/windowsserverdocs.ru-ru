---
title: bootcfg copy
description: Раздел команд Windows для bootcfg Copy, который создает копию существующей загрузочной записи, в которую можно добавить параметры командной строки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2a236c2a-8675-444d-b695-9cbc9aff643b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5194418a07aece4f15a84c3eccbc044431a865b9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848687"
---
# <a name="bootcfg-copy"></a>bootcfg copy

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает копию существующей записи загрузки, в которую можно добавить параметры командной строки.

## <a name="syntax"></a>Синтаксис
```
bootcfg /copy [/s <computer> [/u <Domain>\<User> /p <Password>]] [/d <Description>] [/id <OSEntryLineNum>]
```
### <a name="parameters"></a>Параметры

|      Параметр       |                                                                                             Описание                                                                                             |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                         Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                          |
| /u <Domain>\\<User>  | Выполняет команду с разрешениями учетной записи пользователя, указанного в <User>или <Domain>\\<User>. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
|    /p <Password>     |                                                        Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                        |
|   /d <Description>   |                                                                    Указывает описание новой записи операционной системы.                                                                    |
| /ID <OSEntryLineNum> |         Указывает номер строки записи операционной системы в разделе [Operating Systems] копируемого файла Boot. ini. Первая строка после заголовка раздела [Operating Systems] — 1.         |
|          /?          |                                                                                Отображает справку в командной строке.                                                                                 |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/Copy** , чтобы скопировать загрузочную запись 1 и ввести \абк Server\\ в качестве описания:
```
bootcfg /copy /d \ABC Server\ /id 1
```
## <a name="additional-references"></a>Дополнительные материалы
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
