---
title: bootcfg copy
description: Раздел Windows команды для **копирования bootcfg** -создается копия существующий элемент, к которому можно добавить параметры командной строки.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a236c2a-8675-444d-b695-9cbc9aff643b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b76ecfe953d1a462e311fdaaeba35e8f962165c4
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434859"
---
# <a name="bootcfg-copy"></a>bootcfg copy

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует существующий элемент, к которому можно добавить параметры командной строки.

## <a name="syntax"></a>Синтаксис
```
bootcfg /copy [/s <computer> [/u <Domain>\<User> /p <Password>]] [/d <Description>] [/id <OSEntryLineNum>]
```
## <a name="parameters"></a>Параметры

|      Параметр       |                                                                                             Описание                                                                                             |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                         Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                          |
| /u <Domain>\\<User>  | Выполняет команду с разрешениями учетной записи пользователя, указанного по <User>или <Domain> \\ <User>. По умолчанию используется разрешения текущего, вошедшего в систему пользователя на компьютере, используя следующую команду. |
|    /p <Password>     |                                                        Указывает пароль для учетной записи пользователя, который указан в **/u** параметра.                                                        |
|   /d <Description>   |                                                                    Указывает описание для новой записи операционной системы.                                                                    |
| /ID <OSEntryLineNum> |         Указывает номер строки записи операционной системы в разделе [operating systems] файла Boot.ini, для копирования. Первая строка после заголовка раздела [операционные системы]-1.         |
|          /?          |                                                                                Отображение справки в командной строке.                                                                                 |

## <a name="BKMK_examples"></a>Примеры
В следующих примерах показано, как можно использовать **неправильный** команду, чтобы скопировать загрузочную запись 1 и введите «\ABC Server\\"как описание:
```
bootcfg /copy /d "\ABC Server\" /id 1
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
