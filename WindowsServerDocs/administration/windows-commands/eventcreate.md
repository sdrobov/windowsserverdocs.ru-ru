---
title: eventcreate
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f2b1b26d-a70e-49a6-832b-91eb5a1a159a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 797298622ba1021caef3d04e2f2f06f016ef6a70
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725763"
---
# <a name="eventcreate"></a>eventcreate



Позволяет администратору создать пользовательское событие в указанном журнале событий. 

## <a name="syntax"></a>Синтаксис

```
eventcreate [/s <Computer> [/u <Domain\User> [/p <Password>]] {[/l {APPLICATION|SYSTEM}]|[/so <SrcName>]} /t {ERROR|WARNING|INFORMATION|SUCCESSAUDIT|FAILUREAUDIT} /id <EventID> /d <Description>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/s \<> компьютера|Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.|
|/u \<домен \ пользователь>|Выполняет команду с разрешениями учетной записи пользователя, указанного \<пользователем> или <домен \ пользователь>. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду.|
|/p \<пароль>|Указывает пароль учетной записи пользователя, указанной в параметре **/u** .|
|/l {система\|приложений}|Указывает имя журнала событий, в котором будет создано событие. Допустимые имена журналов — APPLICATION и SYSTEM.|
|/So \<сркнаме>|Указывает источник, используемый для события. Допустимым источником может быть любая строка, которая должна представлять приложение или компонент, создающий событие.|
|/t {\|сведения\|об ошибке\|</br>SUCCESSAUDIT\|FAILUREAUDIT}|Указывает тип создаваемого события. Допустимые типы: ERROR, WARNING, INFORMATION, SUCCESSAUDIT и FAILUREAUDIT.|
|/ID \<>|Указывает идентификатор события для события. Допустимый идентификатор — любое число от 1 до 1000.|
|/d \<описание>|Указывает описание, используемое для вновь созданного события.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Пользовательские события не могут быть записаны в журнал безопасности.

## <a name="examples"></a>Примеры

В следующих примерах показано, как можно использовать команду eventcreate:
```
eventcreate /t error /id 100 /l application /d Create event in application log
eventcreate /t information /id 1000 /so winmgmt /d Create event in WinMgmt source
eventcreate /t error /id 2001 /so winword /l application /d new src Winword in application log
eventcreate /s server /t error /id 100 /l application /d Remote machine without user credentials
eventcreate /s server /u user /p password /id 100 /t error /l application /d Remote machine with user credentials
eventcreate /s server1 /s server2 /u user /p password /id 100 /t error /so winmgmt /d Creating events on Multiple remote machines
eventcreate /s server /u user /id 100 /t warning /so winmgmt /d Remote machine with partial user credentials
```

#### <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
