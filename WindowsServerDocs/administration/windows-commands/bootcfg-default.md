---
title: bootcfg default
description: Раздел команд Windows для **bootcfg default** — указывает запись операционной системы, которую следует назначить по умолчанию.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e21824d7-8278-41d7-a2c5-ce09803d513a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e69868739a9c338b711984ba0f03452f307b430b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380023"
---
# <a name="bootcfg-default"></a>bootcfg default

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Указывает запись операционной системы, которую следует назначить по умолчанию.

## <a name="syntax"></a>Синтаксис
```
bootcfg /default [/s <computer> [/u <Domain>\<User> /p <Password>]] [/id <OSEntryLineNum>]
```
## <a name="parameters"></a>Параметры

|      Параметр       |                                                                                             Описание                                                                                              |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                          Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                          |
| /u <Domain> @ no__t-1 @ no__t-2  | Выполняет команду с разрешениями учетной записи пользователя, заданного <User> или <Domain> @ no__t-2 @ no__t-3. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
|    /p <Password>     |                                                        Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                         |
| /ID <OSEntryLineNum> | Указывает номер строки записи операционной системы в разделе [Operating Systems] файла Boot. ini для обозначения по умолчанию. Первая строка после заголовка раздела [Operating Systems] — 1.  |
|          /?          |                                                                                 Отображение справки в командной строке.                                                                                 |

## <a name="BKMK_examples"></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/default**:
```
bootcfg /default /id 2
bootcfg /default /s srvmain /u maindom\hiropln /p p@ssW23 /id 2
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
