---
title: bootcfg delete
description: Раздел Windows команды для **удалить bootcfg** -удаляет записи операционной системы в разделе операционных систем в файле Boot.ini.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 37f30a181402fe8a74148b42398641af3c4846b9
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434764"
---
# <a name="bootcfg-delete"></a>bootcfg delete

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет запись операционной системы в разделе [operating systems] файла Boot.ini.

## <a name="syntax"></a>Синтаксис
```
bootcfg /delete [/s <computer> [/u <Domain>\<User> /p <Password>]] [/id <OSEntryLineNum>]
```
## <a name="parameters"></a>Параметры

|         Термин         |                                                                                             Определение                                                                                              |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                         Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                          |
| /u <Domain>\\<User>  | Выполняет команду с разрешениями учетной записи пользователя, указанного по <User>или <Domain> \\ <User>. По умолчанию используется разрешения текущего, вошедшего в систему пользователя на компьютере, используя следующую команду. |
|    /p <Password>     |                                                        Указывает пароль для учетной записи пользователя, который указан в **/u** параметра.                                                        |
| /ID <OSEntryLineNum> |        Указывает номер строки записи операционной системы в разделе [operating systems] файла Boot.ini, для удаления. Первая строка после заголовка раздела [операционные системы]-1.        |
|          /?          |                                                                                Отображение справки в командной строке.                                                                                 |

## <a name="BKMK_examples"></a>Примеры
В следующих примерах показано, как можно использовать **неправильный**команды:
```
bootcfg /delete /id 1
bootcfg /delete /s srvmain /u maindom\hiropln /p p@ssW23 /id 3
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
