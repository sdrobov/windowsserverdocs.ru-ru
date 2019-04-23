---
title: Настройка Scwcmd
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6528b9dc-3d82-4228-b734-ed717458d74c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 31838ac7299cc30a7b7dde3beb47669df772487c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59857505"
---
# <a name="scwcmd-configure"></a>Scwcmd: configure

> Область применения. Windows Server 2012 R2, Windows Server 2012

Применяет политику безопасности, созданные с помощью мастера настройки безопасности SCW на компьютере. Это средство командной строки также принимает список имен компьютеров в качестве входных данных.

## <a name="syntax"></a>Синтаксис

```
scwcmd configure [[[/m:<ComputerName> | /ou:<OuName>] /p:<Policy>] | /i:<ComputerList>] [/u:<UserName>] [/pw:<Password>] [/t:<Threads>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/ m:\<имя_компьютера >|Указывает NetBIOS-имя, DNS-имя или IP-адрес компьютера для настройки. Если **/m** параметр указан, то **/p** необходимо также указать параметр.|
|/ OU:\<OuName >|Указывает полное доменное имя (FQDN) подразделения (OU) в доменных службах Active Directory. Если **/ou** параметр указан, то **/p** необходимо также указать параметр. В соответствии с заданной политикой будут проанализированы все компьютеры в Подразделении.|
|/ p:\<политики >|Указывает путь и имя XML-файла политики, который будет использоваться для выполнения настройки.|
|/i:\<ComputerList>|Указывает путь и имя XML-файл, содержащий список компьютеров вместе с соответствующими файлами ожидаемый политики. Все компьютеры в XML-файле будут настроены в соответствии с соответствующими им файлами политики. В образце XML-файл является % windir%\security\SampleMachineList.xml.|
|/u:\<UserName>|Указывает это учетные данные другого пользователя, используемое при настройке удаленного компьютера. По умолчанию используется вошедшего пользователя.|
|/ PW:\<пароль >|Указывает это учетные данные другого пользователя, используемое при настройке удаленного компьютера. Значение по умолчанию — пароль пользователя, вошедшего в систему.|
|/ t:\<потоки >|Указывает количество одновременных необработанных операций, которые должны сохраняться во время процесса настройки (DefaultValue = 40, MinValue = 1, MaxValue = 1000).|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Scwcmd.exe доступна только на компьютерах под управлением Windows Server 2008 R2, Windows Server 2008 или Windows Server 2003.

## <a name="BKMK_Examples"></a>Примеры

Чтобы настроить политику безопасности, используя файл webpolicy.xml, введите следующую команду:
```
scwcmd configure /p:webpolicy.xml
```
Чтобы настроить политику безопасности для компьютера на 172.16.0.0 от webpolicy.xml файл, используя учетные данные учетной записи webadmin, введите следующую команду:
```
scwcmd configure /m:172.16.0.0 /p:webpolicy.xml /u:webadmin
```
Чтобы настроить политику безопасности на всех компьютерах campusmachines.xml списка, не более 100 потоков, введите следующую команду:
```
scwcmd configure /i:campusmachines.xml /t:100
```
Чтобы настроить политику безопасности на всех компьютерах в Подразделении веб-серверы от webpolicy.xml файл, используя учетные данные учетной записи DomainAdmin, введите следующую команду:
```
scwcmd configure /ou:OU=WebServers,DC=Marketing,DC=ABCCompany,DC=com /p:webpolicy.xml /u:DomainAdmin
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)