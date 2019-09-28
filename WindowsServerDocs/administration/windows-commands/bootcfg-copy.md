---
title: bootcfg copy
description: Раздел команд Windows для **bootcfg Copy** — создает копию существующей загрузочной записи, в которую можно добавить параметры командной строки.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a236c2a-8675-444d-b695-9cbc9aff643b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 42a408443cbe6722c25780f7c27d70b05da7eb8e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380116"
---
# <a name="bootcfg-copy"></a>bootcfg copy

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает копию существующей записи загрузки, в которую можно добавить параметры командной строки.

## <a name="syntax"></a>Синтаксис
```
bootcfg /copy [/s <computer> [/u <Domain>\<User> /p <Password>]] [/d <Description>] [/id <OSEntryLineNum>]
```
## <a name="parameters"></a>Параметры

|      Параметр       |                                                                                             Описание                                                                                             |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                         Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                          |
| /u <Domain> @ no__t-1 @ no__t-2  | Выполняет команду с разрешениями учетной записи пользователя, заданного <User>or <Domain> @ no__t-2 @ no__t-3. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
|    /p <Password>     |                                                        Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                        |
|   /d <Description>   |                                                                    Указывает описание новой записи операционной системы.                                                                    |
| /ID <OSEntryLineNum> |         Указывает номер строки записи операционной системы в разделе [Operating Systems] копируемого файла Boot. ini. Первая строка после заголовка раздела [Operating Systems] — 1.         |
|          /?          |                                                                                Отображение справки в командной строке.                                                                                 |

## <a name="BKMK_examples"></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/Copy** , чтобы скопировать загрузочную запись 1, и в качестве описания введите "\абк Server @ no__t-1".
```
bootcfg /copy /d "\ABC Server\" /id 1
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
