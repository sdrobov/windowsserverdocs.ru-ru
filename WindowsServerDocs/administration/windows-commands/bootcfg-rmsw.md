---
title: bootcfg rmsw
description: Раздел команд Windows для bootcfg рмсв, который удаляет параметры загрузки операционной системы для указанной записи операционной системы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fd7e4248-880e-4e2b-929e-87f8d44b9a63
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 956732f396e0fa353a8acd55953e46605a5c4200
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848447"
---
# <a name="bootcfg-rmsw"></a>bootcfg rmsw

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет параметры загрузки операционной системы для указанной записи операционной системы.

## <a name="syntax"></a>Синтаксис
```
bootcfg /rmsw [/s <computer> [/u <Domain>\<User> [/p <Password>]]] [/mm] [/bv] [/so] [/ng] /id <OSEntryLineNum>
```
### <a name="parameters"></a>Параметры

|      Параметр       |                                                                                                      Описание                                                                                                       |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                                   Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                                   |
| /u <Domain>\\<User>  |          Выполняет команду с разрешениями учетной записи пользователя, указанного в <User> или <Domain>\\<User>. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду.          |
|    /p <Password>     |                                                                 Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                                  |
|         /mm          |           Удаляет параметр/maxmem и связанное с ним максимальное значение памяти из указанного <OSEntryLineNum>. Параметр/maxmem указывает максимальный объем ОЗУ, который может использовать операционная система.            |
|         /bv          |                     Удаляет параметр/басевидео из указанного <OSEntryLineNum>. Параметр/басевидео указывает операционной системе использовать стандартный режим VGA для установленного видеодрайвера.                     |
|         /So          |                         Удаляет параметр/SOS из указанного <OSEntryLineNum>. Параметр/SOS указывает операционной системе отображать имена драйверов устройств во время их загрузки.                          |
|         /NG          |                         Удаляет параметр/ногуибут из указанного <OSEntryLineNum>. Параметр/ногуибут отключает индикатор выполнения, который отображается перед запросом CTRL + ALT + DEL для входа.                          |
| /ID <OSEntryLineNum> | Указывает номер строки записи операционной системы в разделе [Operating Systems] файла Boot. ini, из которого удаляются параметры загрузки ОС. Первая строка после заголовка раздела [Operating Systems] — 1. |
|          /?          |                                                                                          Отображает справку в командной строке.                                                                                          |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/rmsw**:
```
bootcfg /rmsw /mm 64 /id 2 
bootcfg /rmsw /so /id 3 
bootcfg /rmsw /so /ng /s srvmain /u hiropln /id 2 
bootcfg /rmsw /ng /id 2 
bootcfg /rmsw /mm 96 /ng /s srvmain /u maindom\hiropln /p p@ssW23 /id 2       
```
## <a name="additional-references"></a>Дополнительные материалы
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
