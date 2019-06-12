---
title: bootcfg addsw
description: Раздел Windows команды для **bootcfg addsw** -добавляет параметры загрузки операционной системы для записи определенной операционной системы.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d8389293-ecd9-42f0-b84b-b9ead4cf52e6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a056cec15bf804dafed4c4d39a80386e58c87fea
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434884"
---
# <a name="bootcfg-addsw"></a>bootcfg addsw

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавление параметров загрузки операционной системы для записи определенной операционной системы.

## <a name="syntax"></a>Синтаксис
```
bootcfg /addsw [/s <computer> [/u <Domain>\<User> /p <Password>]] [/mm <MaximumRAM>] [/bv] [/so] [/ng] /id <OSEntryLineNum>
```
## <a name="parameters"></a>Параметры

|         Термин         |                                                                                                            Определение                                                                                                            |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                                        Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                                        |
| /u <Domain>\\<User>  |               Выполняет команду с разрешениями учетной записи пользователя, указанного по <User> или <Domain> \\ <User>. По умолчанию используется разрешения текущего, вошедшего в систему пользователя на компьютере, используя следующую команду.               |
|    /p <Password>     |                                                                      Указывает пароль для учетной записи пользователя, который указан в **/u** параметра.                                                                       |
|   /mm <MaximumRAM>   |                                          Указывает максимальный объем ОЗУ, в мегабайтах, которые может использовать операционную систему. Значение должно быть равно или больше, чем 32 МБ.                                          |
|         /bv          |                                    Добавляет **ключа/basevideo** параметр в указанном <OSEntryLineNum>, задает в операционной системе для использования стандартного режима VGA для установленного видеодрайвера.                                     |
|         /SO          |                                      Добавляет **/SOS** параметр в указанном *Номер_строки_записи_в_разделе_ос*, задает в операционной системе для отображения имен драйверов устройств при их загрузке.                                      |
|         /ng          |                                         Добавляет **/noguiboot** параметр в указанном <OSEntryLineNum>, отключение индикатор выполнения, отображается перед CTRL + ALT + del входа prompt.                                          |
| /ID <OSEntryLineNum> | Указывает номер строки записи операционной системы в разделе [operating systems] файла Boot.ini, к которому добавляются параметры загрузки операционной системы. Первая строка после заголовка раздела [операционные системы]-1. |
|          /?          |                                                                                               Отображение справки в командной строке.                                                                                               |

## <a name="BKMK_examples"></a>Примеры
В следующих примерах показано, как можно использовать **неверный** команды:
```
bootcfg /addsw /mm 64 /id 2 
bootcfg /addsw /so /id 3 
bootcfg /addsw /so /ng /s srvmain /u hiropln /id 2 
bootcfg /addsw /ng /id 2 
bootcfg /addsw /mm 96 /ng /s srvmain /u maindom\hiropln /p p@ssW23 /id 2
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
