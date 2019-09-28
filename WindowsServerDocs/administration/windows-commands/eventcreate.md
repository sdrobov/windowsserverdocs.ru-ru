---
title: eventcreate
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f2b1b26d-a70e-49a6-832b-91eb5a1a159a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cf53d8d269d0994ddf57eb350982effed5e0e702
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377522"
---
# <a name="eventcreate"></a>eventcreate



Позволяет администратору создать пользовательское событие в указанном журнале событий. В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
eventcreate [/s <Computer> [/u <Domain\User> [/p <Password>]] {[/l {APPLICATION|SYSTEM}]|[/so <SrcName>]} /t {ERROR|WARNING|INFORMATION|SUCCESSAUDIT|FAILUREAUDIT} /id <EventID> /d <Description>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/s @no__t 0Computer >|Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.|
|/u \<Domain \ пользователь >|Выполняет команду с разрешениями учетной записи пользователя, указанного в \<User > или < домен \ пользователь >. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду.|
|/p \<пароль >|Указывает пароль учетной записи пользователя, указанной в параметре **/u** .|
|/l {APPLICATION @ no__t-0SYSTEM}|Указывает имя журнала событий, в котором будет создано событие. Допустимые имена журналов — APPLICATION и SYSTEM.|
|/So @no__t — 0SrcName >|Указывает источник, используемый для события. Допустимым источником может быть любая строка, которая должна представлять приложение или компонент, создающий событие.|
|/t {ERROR @ no__t-0WARNING @ no__t-1INFORMATION @ no__t-2</br>SUCCESSAUDIT @ NO__T-0FAILUREAUDIT}|Указывает тип создаваемого события. Допустимые типы: ERROR, WARNING, INFORMATION, SUCCESSAUDIT и FAILUREAUDIT.|
|/ID \<EventID >|Указывает идентификатор события для события. Допустимый идентификатор — любое число от 1 до 1000.|
|/d \<Description >|Указывает описание, используемое для вновь созданного события.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Пользовательские события не могут быть записаны в журнал безопасности.

## <a name="BKMK_examples"></a>Примеров

В следующих примерах показано, как можно использовать команду eventcreate:
```
eventcreate /t error /id 100 /l application /d "Create event in application log"
eventcreate /t information /id 1000 /so winmgmt /d "Create event in WinMgmt source"
eventcreate /t error /id 2001 /so winword /l application /d "new src Winword in application log"
eventcreate /s server /t error /id 100 /l application /d "Remote machine without user credentials"
eventcreate /s server /u user /p password /id 100 /t error /l application /d "Remote machine with user credentials"
eventcreate /s server1 /s server2 /u user /p password /id 100 /t error /so winmgmt /d "Creating events on Multiple remote machines"
eventcreate /s server /u user /id 100 /t warning /so winmgmt /d "Remote machine with partial user credentials"
```

#### <a name="additional-references"></a>Дополнительные ссылки

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
