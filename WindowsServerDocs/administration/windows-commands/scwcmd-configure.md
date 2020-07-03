---
title: Настройка команду scwcmd
description: Справочная статья для * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6528b9dc-3d82-4228-b734-ed717458d74c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e93c0566c28cc77074781b4670dac689795aeeb2
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932667"
---
# <a name="scwcmd-configure"></a>Scwcmd: configure

> Область применения: Windows Server 2012 R2, Windows Server 2012

Применяет к компьютеру политику безопасности, созданную с помощью мастера настройки безопасности (SCW). Это средство командной строки также принимает список имен компьютеров в качестве входных данных.

## <a name="syntax"></a>Синтаксис

```
scwcmd configure [[[/m:<ComputerName> | /ou:<OuName>] /p:<Policy>] | /i:<ComputerList>] [/u:<UserName>] [/pw:<Password>] [/t:<Threads>]
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/m\<ComputerName>|Указывает имя NetBIOS, DNS-имя или IP-адрес компьютера для настройки. Если указан параметр **/m** , необходимо также указать параметр **/p** .|
|/OU\<OuName>|Указывает полное доменное имя подразделения (OU) в домен Active Directory Services. Если указан параметр **/OU** , необходимо также указать параметр **/p** . Все компьютеры в подразделении будут анализироваться в соответствии с заданной политикой.|
|/p\<Policy>|Указывает путь и имя файла политики XML, который будет использоваться для выполнения настройки.|
|/i\<ComputerList>|Указывает путь и имя XML-файла, содержащего список компьютеров вместе с ожидаемыми файлами политики. Все компьютеры в XML-файле будут настроены в соответствии с соответствующими файлами политики. Пример XML-файла —% WINDIR% \security\SampleMachineList.xml.|
|/u\<UserName>|Указывает альтернативные учетные данные пользователя для использования при настройке удаленного компьютера. Значение по умолчанию — вошедший в систему пользователь.|
|пароль\<Password>|Указывает альтернативные учетные данные пользователя для использования при настройке удаленного компьютера. По умолчанию используется пароль пользователя, выполнившего вход.|
|/t:\<Threads>|Указывает количество одновременных операций настройки, которые должны поддерживаться в процессе настройки (DefaultValue = 40, MinValue = 1, MaxValue = 1000).|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Комментарии

Scwcmd.exe доступны только на компьютерах под управлением Windows Server 2008 R2, Windows Server 2008 или Windows Server 2003.

## <a name="examples"></a>Примеры

Чтобы настроить политику безопасности для webpolicy.xml файлов, введите:
```
scwcmd configure /p:webpolicy.xml
```
Чтобы настроить политику безопасности для компьютера с параметром 172.16.0.0 в отношении файла webpolicy.xml с помощью учетных данных учетной записи вебадмин, введите:
```
scwcmd configure /m:172.16.0.0 /p:webpolicy.xml /u:webadmin
```
Чтобы настроить политику безопасности на всех компьютерах в списке campusmachines.xml с максимум 100 потоками, введите:
```
scwcmd configure /i:campusmachines.xml /t:100
```
Чтобы настроить политику безопасности на всех компьютерах подразделения "webpolicy.xml" с помощью учетных данных учетной записи DomainAdmin, введите:
```
scwcmd configure /ou:OU=WebServers,DC=Marketing,DC=ABCCompany,DC=com /p:webpolicy.xml /u:DomainAdmin
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)