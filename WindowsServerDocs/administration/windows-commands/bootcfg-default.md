---
title: bootcfg default
description: Раздел команд Windows для bootcfg default, который указывает запись операционной системы, которую следует назначить по умолчанию.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e21824d7-8278-41d7-a2c5-ce09803d513a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 517cf444a5517b3d612266b57b428e47ac60d4ef
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848568"
---
# <a name="bootcfg-default"></a>bootcfg default

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Указывает запись операционной системы, которую следует назначить по умолчанию.

## <a name="syntax"></a>Синтаксис
```
bootcfg /default [/s <computer> [/u <Domain>\<User> /p <Password>]] [/id <OSEntryLineNum>]
```
### <a name="parameters"></a>Параметры

|      Параметр       |                                                                                             Описание                                                                                              |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                          Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                          |
| /u <Domain>\\<User>  | Выполняет команду с разрешениями учетной записи пользователя, указанного в <User> или <Domain>\\<User>. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
|    /p <Password>     |                                                        Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                         |
| /ID <OSEntryLineNum> | Указывает номер строки записи операционной системы в разделе [Operating Systems] файла Boot. ini для обозначения по умолчанию. Первая строка после заголовка раздела [Operating Systems] — 1.  |
|          /?          |                                                                                 Отображает справку в командной строке.                                                                                 |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/default**:
```
bootcfg /default /id 2
bootcfg /default /s srvmain /u maindom\hiropln /p p@ssW23 /id 2
```
## <a name="additional-references"></a>Дополнительные материалы
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
