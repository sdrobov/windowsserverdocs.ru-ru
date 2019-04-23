---
title: bootcfg rmsw
description: Раздел Windows команды для **bootcfg rmsw** — удаляет операционной системы параметры загрузки для записи определенной операционной системы.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fd7e4248-880e-4e2b-929e-87f8d44b9a63
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 65a8ba452911eb1b46a748d4e9d639ed102421b6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59878825"
---
# <a name="bootcfg-rmsw"></a>bootcfg rmsw

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет параметры загрузки операционной системы для записи определенной операционной системы.

## <a name="syntax"></a>Синтаксис
```
bootcfg /rmsw [/s <computer> [/u <Domain>\<User> [/p <Password>]]] [/mm] [/bv] [/so] [/ng] /id <OSEntryLineNum>
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/s <computer>|Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.|
|/u <Domain>\\<User>|Выполняет команду с разрешениями учетной записи пользователя, указанного по <User> или <Domain> \\ <User>. По умолчанию используется разрешения текущего, вошедшего в систему пользователя на компьютере, используя следующую команду.|
|/p <Password>|Указывает пароль для учетной записи пользователя, который указан в **/u** параметра.|
|/mm|Удаляет maxmem и его значение максимального объема памяти из заданного <OSEntryLineNum>. Параметр/maxmem указывает максимальный объем ОЗУ, можно использовать операционной системы.|
|/bv|Удаляет из указанного параметра ключа/basevideo <OSEntryLineNum>. / Basevideo операционной системы для использования стандартного режима VGA для установленного видеодрайвера.|
|/SO|Удаляет параметр/SOS из указанного <OSEntryLineNum>. SOS задает операционной системы для отображения имен драйверов устройств при их загрузке.|
|/ng|Удаляет параметр/noguiboot из указанного <OSEntryLineNum>. / Noguiboot отключает индикатор выполнения, отображается перед CTRL + ALT + del входа в систему.|
|/ID <OSEntryLineNum>|Указывает номер строки записи операционной системы в разделе [operating systems] файла Boot.ini, из которого удаляются параметры загрузки ОС. Первая строка после заголовка раздела [операционные системы]-1.|
|/?|Отображение справки в командной строке.|
## <a name="BKMK_examples"></a>Примеры
В следующих примерах показано, как можно использовать **неправильный**команды:
```
bootcfg /rmsw /mm 64 /id 2 
bootcfg /rmsw /so /id 3 
bootcfg /rmsw /so /ng /s srvmain /u hiropln /id 2 
bootcfg /rmsw /ng /id 2 
bootcfg /rmsw /mm 96 /ng /s srvmain /u maindom\hiropln /p p@ssW23 /id 2       
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
