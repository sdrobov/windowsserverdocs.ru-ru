---
title: bootcfg delete
description: Раздел команд Windows для **bootcfg Delete** — удаляет запись операционной системы в разделе операционных систем файла Boot. ini.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71382e29-9b39-41c8-9c23-cf0ff829440a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7d2298c07af32e66a2ffcebb85ec780da762be58
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380010"
---
# <a name="bootcfg-delete"></a>bootcfg delete

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет запись операционной системы в разделе [Operating Systems] файла Boot. ini.

## <a name="syntax"></a>Синтаксис
```
bootcfg /delete [/s <computer> [/u <Domain>\<User> /p <Password>]] [/id <OSEntryLineNum>]
```
## <a name="parameters"></a>Параметры

|         Термин         |                                                                                             Определение                                                                                              |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                         Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                          |
| /u <Domain> @ no__t-1 @ no__t-2  | Выполняет команду с разрешениями учетной записи пользователя, заданного <User>or <Domain> @ no__t-2 @ no__t-3. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
|    /p <Password>     |                                                        Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                        |
| /ID <OSEntryLineNum> |        Указывает номер строки записи операционной системы в разделе [Operating Systems] файла Boot. ini, который необходимо удалить. Первая строка после заголовка раздела [Operating Systems] — 1.        |
|          /?          |                                                                                Отображение справки в командной строке.                                                                                 |

## <a name="BKMK_examples"></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/Delete**:
```
bootcfg /delete /id 1
bootcfg /delete /s srvmain /u maindom\hiropln /p p@ssW23 /id 3
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
