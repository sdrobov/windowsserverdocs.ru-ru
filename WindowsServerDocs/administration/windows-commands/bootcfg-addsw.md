---
title: bootcfg addsw
description: Раздел команд Windows для bootcfg аддсв, который добавляет параметры загрузки операционной системы для указанной записи операционной системы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d8389293-ecd9-42f0-b84b-b9ead4cf52e6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a9ae5175dfc3b068276f6ab95d6823699c96b2b5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848717"
---
# <a name="bootcfg-addsw"></a>bootcfg addsw

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет параметры загрузки операционной системы для указанной записи операционной системы.

## <a name="syntax"></a>Синтаксис
```
bootcfg /addsw [/s <computer> [/u <Domain>\<User> /p <Password>]] [/mm <MaximumRAM>] [/bv] [/so] [/ng] /id <OSEntryLineNum>
```
### <a name="parameters"></a>Параметры

|         Термин         |                                                                                                            Определение                                                                                                            |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                                        Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                                        |
| /u <Domain>\\<User>  |               Выполняет команду с разрешениями учетной записи пользователя, указанного в <User> или <Domain>\\<User>. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду.               |
|    /p <Password>     |                                                                      Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                                       |
|   /mm <MaximumRAM>   |                                          Указывает максимальный объем ОЗУ в мегабайтах, который может использоваться операционной системой. Значение должно быть больше или равно 32 МБ.                                          |
|         /bv          |                                    Добавляет параметр **/басевидео** к указанному <OSEntryLineNum>, направляя операционную систему для использования стандартного режима VGA для установленного видеодрайвера.                                     |
|         /So          |                                      Добавляет параметр **/SOS** в указанную *номер_строки_записи_в_разделе_ОС*, направляя операционную систему на отображение имен драйверов устройств во время их загрузки.                                      |
|         /NG          |                                         Добавляет параметр **/ногуибут** к заданному <OSEntryLineNum>, отключая индикатор выполнения, который отображается перед запросом Ctrl + Alt + Del для входа.                                          |
| /ID <OSEntryLineNum> | Указывает номер строки записи операционной системы в разделе [Operating Systems] файла Boot. ini, в который добавляются параметры загрузки операционной системы. Первая строка после заголовка раздела [Operating Systems] — 1. |
|          /?          |                                                                                               Отображает справку в командной строке.                                                                                               |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/ADDSW** :
```
bootcfg /addsw /mm 64 /id 2 
bootcfg /addsw /so /id 3 
bootcfg /addsw /so /ng /s srvmain /u hiropln /id 2 
bootcfg /addsw /ng /id 2 
bootcfg /addsw /mm 96 /ng /s srvmain /u maindom\hiropln /p p@ssW23 /id 2
```
## <a name="additional-references"></a>Дополнительные материалы
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
