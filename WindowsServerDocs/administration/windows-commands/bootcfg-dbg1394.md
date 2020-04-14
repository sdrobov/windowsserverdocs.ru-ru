---
title: bootcfg dbg1394
description: Раздел команд Windows для bootcfg dbg1394, который настраивает отладку портов 1394 для указанной записи операционной системы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 35724697-90dd-4dbe-85b0-337fbd369dcc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d49e0a39cd021f093ca68bf97963dc35c3b53ad4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848677"
---
# <a name="bootcfg-dbg1394"></a>bootcfg dbg1394

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Настраивает отладку порта 1394 для указанной записи операционной системы.

## <a name="syntax"></a>Синтаксис
```
bootcfg /dbg1394 {ON | OFF}[/s <computer> [/u <Domain>\<User> /p <Password>]] [/ch <Channel>] /id <OSEntryLineNum>
```
### <a name="parameters"></a>Параметры

|      Параметр       |                                                                                                                                           Описание                                                                                                                                            |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   {ON &#124; Off}    | Указывает значение для отладки порта 1394.<p>-   **On** — включение поддержки удаленной отладки путем добавления параметра/dbg1394 в указанный <OSEntryLineNum>.<br />-   **Off** — отключает поддержку удаленной отладки путем удаления параметра/dbg1394 из указанного <OSEntryLineNum>. |
|    /s <computer>     |                                                                                        Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                                                                        |
| /u <Domain>\\<User>  |                                               Выполняет команду с разрешениями учетной записи пользователя, указанного в <User> или <Domain>\\<User>. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду.                                               |
|    /p <Password>     |                                                                                                      Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                                                                       |
|     Канал/ч      |                                                           Указывает канал, используемый для отладки. Допустимые значения — целые числа в диапазоне от 1 до 64. Не используйте параметр <Channel> **/ч** , если отключена отладка порта 1394.                                                           |
| /ID <OSEntryLineNum> |                                  Указывает номер строки записи операционной системы в разделе [Operating Systems] файла Boot. ini, в который добавляются параметры отладки порта 1394. Первая строка после заголовка раздела [Operating Systems] — 1.                                  |
|          /?          |                                                                                                                               Отображает справку в командной строке.                                                                                                                               |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/dbg1394**.
```
bootcfg /dbg1394 /id 2 
bootcfg /dbg1394 on /ch 1 /id 3 
bootcfg /dbg1394 edit /ch 8 /id 2 
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /dbg1394 off /id 2
```
## <a name="additional-references"></a>Дополнительные материалы
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
