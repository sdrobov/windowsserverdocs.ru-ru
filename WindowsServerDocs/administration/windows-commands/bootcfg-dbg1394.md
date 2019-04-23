---
title: bootcfg dbg1394
description: Раздел Windows команды для **bootcfg dbg1394** -1394 настраивает порт отладки для определенной записи операционной системы
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35724697-90dd-4dbe-85b0-337fbd369dcc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b36d22cea5b7b0c0e1768736d6c80c67b3c733f9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59857655"
---
# <a name="bootcfg-dbg1394"></a>bootcfg dbg1394

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Настройка отладки порта 1394 для определенной записи операционной системы.

## <a name="syntax"></a>Синтаксис
```
bootcfg /dbg1394 {ON | OFF}[/s <computer> [/u <Domain>\<User> /p <Password>]] [/ch <Channel>] /id <OSEntryLineNum>
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|{ON &#124; OFF}|Указывает значения для отладки 1394 порта.<br /><br />-   **ON** -Включение поддержки удаленной отладки, добавив параметр/DBG1394 в указанный <OSEntryLineNum>.<br />-   **ОТКЛЮЧЕНИЕ** -отключение поддержки удаленной отладки путем удаления из указанного параметра/DBG1394 <OSEntryLineNum>.|
|/s <computer>|Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.|
|/u <Domain>\\<User>|Выполняет команду с разрешениями учетной записи пользователя, указанного по <User> или <Domain> \\ <User>. По умолчанию используется разрешения текущего, вошедшего в систему пользователя на компьютере, используя следующую команду.|
|/p <Password>|Указывает пароль для учетной записи пользователя, который указан в **/u** параметра.|
|/CH канал|Указывает канал, который нужно использовать для отладки. Допустимые значения: целые числа от 1 до 64. Не используйте **/ch** <Channel> параметра, если отладка порта 1394 отключена.|
|/ID <OSEntryLineNum>|Указывает номер строки записи операционной системы в разделе [operating systems] файла Boot.ini, к которому добавляются параметры отладки порта 1394. Первая строка после заголовка раздела [операционные системы]-1.|
|/?|Отображение справки в командной строке.|
## <a name="BKMK_examples"></a>Примеры
В следующих примерах показано, как можно использовать **bootcfg/DBG1394**команды:
```
bootcfg /dbg1394 /id 2 
bootcfg /dbg1394 on /ch 1 /id 3 
bootcfg /dbg1394 edit /ch 8 /id 2 
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /dbg1394 off /id 2
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
