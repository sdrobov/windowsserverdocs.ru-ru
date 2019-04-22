---
title: bootcfg default
description: Раздел Windows команды для **по умолчанию bootcfg** -указывает запись операционной системы, используемой по умолчанию.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e21824d7-8278-41d7-a2c5-ce09803d513a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: aa19c787182584e941850bb38e6c4e8006790fca
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59823155"
---
# <a name="bootcfg-default"></a>bootcfg default

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Указывает запись операционной системы, используемой по умолчанию.

## <a name="syntax"></a>Синтаксис
```
bootcfg /default [/s <computer> [/u <Domain>\<User> /p <Password>]] [/id <OSEntryLineNum>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/s <computer>|Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.|
|/u <Domain>\\<User>|Выполняет команду с разрешениями учетной записи пользователя, указанного по <User> или <Domain> \\ <User>. По умолчанию используется разрешения текущего, вошедшего в систему пользователя на компьютере, используя следующую команду.|
|/p <Password>|Указывает пароль для учетной записи пользователя, который указан в **/u** параметра.|
|/ID <OSEntryLineNum>|Указывает номер строки записи операционной системы в разделе [operating systems] файла Boot.ini, используемой по умолчанию. Первая строка после заголовка раздела [операционные системы]-1.|
|/?|Отображение справки в командной строке.|
## <a name="BKMK_examples"></a>Примеры
В следующих примерах показано, как можно использовать **/Default bootcfg**команды:
```
bootcfg /default /id 2
bootcfg /default /s srvmain /u maindom\hiropln /p p@ssW23 /id 2
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
