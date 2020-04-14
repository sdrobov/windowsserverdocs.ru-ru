---
title: eventcreate
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f2b1b26d-a70e-49a6-832b-91eb5a1a159a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 79b10963abef9918e5962fdaf7d387a129873452
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80845097"
---
# <a name="eventcreate"></a>eventcreate



Позволяет администратору создать пользовательское событие в указанном журнале событий. В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
eventcreate [/s <Computer> [/u <Domain\User> [/p <Password>]] {[/l {APPLICATION|SYSTEM}]|[/so <SrcName>]} /t {ERROR|WARNING|INFORMATION|SUCCESSAUDIT|FAILUREAUDIT} /id <EventID> /d <Description>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/s \<> компьютера|Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.|
|/u \<домен \ пользователь >|Выполняет команду с разрешениями учетной записи пользователя, указанного пользователем \<пользователь > или < домен \ пользователь >. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду.|
|/p \<пароль >|Указывает пароль учетной записи пользователя, указанной в параметре **/u** .|
|/l {система\|приложений}|Указывает имя журнала событий, в котором будет создано событие. Допустимые имена журналов — APPLICATION и SYSTEM.|
|/So \<Сркнаме >|Указывает источник, используемый для события. Допустимым источником может быть любая строка, которая должна представлять приложение или компонент, создающий событие.|
|/t {ошибка\|\|сведения о ПРЕДУПРЕЖДЕНИи\|</br>SUCCESSAUDIT\|FAILUREAUDIT}|Указывает тип создаваемого события. Допустимые типы: ERROR, WARNING, INFORMATION, SUCCESSAUDIT и FAILUREAUDIT.|
|/ID \<> EventID|Указывает идентификатор события для события. Допустимый идентификатор — любое число от 1 до 1000.|
|/d \<описание >|Указывает описание, используемое для вновь созданного события.|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

-   Пользовательские события не могут быть записаны в журнал безопасности.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

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

#### <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
