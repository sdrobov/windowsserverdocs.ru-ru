---
title: bootcfg delete
description: Раздел команд Windows для bootcfg DELETE, который удаляет запись операционной системы в разделе "операционные системы" файла Boot. ini.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 71382e29-9b39-41c8-9c23-cf0ff829440a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 01ec7a4dde1e22982f2cf0fa30245c33e09cc0ff
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848547"
---
# <a name="bootcfg-delete"></a>bootcfg delete

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет запись операционной системы в разделе [Operating Systems] файла Boot. ini.

## <a name="syntax"></a>Синтаксис
```
bootcfg /delete [/s <computer> [/u <Domain>\<User> /p <Password>]] [/id <OSEntryLineNum>]
```
### <a name="parameters"></a>Параметры

|         Термин         |                                                                                             Определение                                                                                              |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                         Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                          |
| /u <Domain>\\<User>  | Выполняет команду с разрешениями учетной записи пользователя, указанного в <User>или <Domain>\\<User>. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
|    /p <Password>     |                                                        Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                        |
| /ID <OSEntryLineNum> |        Указывает номер строки записи операционной системы в разделе [Operating Systems] файла Boot. ini, который необходимо удалить. Первая строка после заголовка раздела [Operating Systems] — 1.        |
|          /?          |                                                                                Отображает справку в командной строке.                                                                                 |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/Delete**:
```
bootcfg /delete /id 1
bootcfg /delete /s srvmain /u maindom\hiropln /p p@ssW23 /id 3
```
## <a name="additional-references"></a>Дополнительные материалы
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
