---
title: bootcfg rmsw
description: Раздел команд Windows для **bootcfg рмсв** — удаление параметров загрузки операционной системы для указанной записи операционной системы.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 43629f2e13bb6269a43d592fa0907637135aea71
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379864"
---
# <a name="bootcfg-rmsw"></a>bootcfg rmsw

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет параметры загрузки операционной системы для указанной записи операционной системы.

## <a name="syntax"></a>Синтаксис
```
bootcfg /rmsw [/s <computer> [/u <Domain>\<User> [/p <Password>]]] [/mm] [/bv] [/so] [/ng] /id <OSEntryLineNum>
```
## <a name="parameters"></a>Параметры

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
|          /?          |                                                                                          Отображение справки в командной строке.                                                                                          |

## <a name="BKMK_examples"></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/rmsw**:
```
bootcfg /rmsw /mm 64 /id 2 
bootcfg /rmsw /so /id 3 
bootcfg /rmsw /so /ng /s srvmain /u hiropln /id 2 
bootcfg /rmsw /ng /id 2 
bootcfg /rmsw /mm 96 /ng /s srvmain /u maindom\hiropln /p p@ssW23 /id 2       
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
