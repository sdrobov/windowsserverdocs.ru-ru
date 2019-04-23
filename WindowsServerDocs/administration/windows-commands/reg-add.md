---
title: Добавление REG
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9ad143e-dc10-4e2e-a229-408393c40079
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 61ed9273c0225477d8bd6043dfc599e3e3ae6228
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868885"
---
# <a name="reg-add"></a>Добавление REG


Добавляет новый подраздел или запись в реестр.

## <a name="syntax"></a>Синтаксис

```
reg add <KeyName> [{/v ValueName | /ve}] [/t DataType] [/s Separator] [/d Data] [/f]
```
В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<keyName*>*|Указывает полный путь к подраздела или записи для добавления. Чтобы указать удаленный компьютер, включают имя компьютера (в формате \\ \\ \<имя_компьютера >\) как часть *KeyName*. Пропуск \\ \\ComputerName\ вызывает операцию по умолчанию на локальном компьютере. *KeyName* должен содержать допустимый корневой раздел. Приведены допустимые корневые ключи для локального компьютера. HKLM, HKCU, HKCR, HKU и HKCC. Если указан удаленный компьютер, являются допустимым корневые ключи: HKLM и HKU. Если имя раздела реестра содержит пробел, заключите имя ключа в кавычки.|
|/v \<ValueName>|Задает имя записи реестра для добавления заданного раздела.|
|/ ve|Указывает, что запись реестра, который добавляется в реестр имеет значение null.|
|/t \<тип >|Указывает тип записи реестра. *Тип* должно быть одно из следующих:</br>REG_SZ</br>REG_MULTI_SZ</br>REG_DWORD_BIG_ENDIAN</br>REG_DWORD</br>REG_BINARY</br>REG_DWORD_LITTLE_ENDIAN</br>REG_LINK</br>REG_FULL_RESOURCE_DESCRIPTOR</br>REG_EXPAND_SZ|
|/s \<разделителя >|Указывает символ, используемый для разделения нескольких экземпляров данных, если задан тип данных REG_MULTI_SZ и более чем одной записи должна быть указана. Если не указан, используется разделитель по умолчанию **\0**.|
|/d \<данных >|Указывает данные для нового раздела реестра.|
|/f|Добавляет запись в реестр без запроса подтверждения.|
|/?|Отображает справку по **reg добавить** в командной строке.|

## <a name="remarks"></a>Примечания

-   Невозможно добавить поддеревьев с этой операцией. Эта версия **reg** не запрашивать подтверждение при добавлении нового раздела.
-   В следующей таблице перечислены возвращаемые значения для **добавьте reg** операции.

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|
-   Для данного типа ключа REG_EXPAND_SZ используйте символ ( **^** ) с **%**«внутри параметра /d

## <a name="BKMK_examples"></a>Примеры

Чтобы добавить ключ HKLM\Software\MyCo на удаленном компьютере ABC, введите следующую команду:
```
REG ADD \\ABC\HKLM\Software\MyCo
```
Добавление записи в реестр HKLM\Software\MyCo со значением с именем **данных** из типа REG_BINARY, данные **fe340ead**, тип:
```
REG ADD HKLM\Software\MyCo /v Data /t REG_BINARY /d fe340ead
```
Добавление HKLM\Software\MyCo Многозначный параметр реестра с именем значение **MRU** из введите REG_MULTI_SZ и данные **fax\0mail\0\0**, тип:
```
REG ADD HKLM\Software\MyCo /v MRU /t REG_MULTI_SZ /d fax\0mail\0\0
```
Добавление HKLM\Software\MyCo запись развернутой реестра с именем значение **путь** из введите REG_EXPAND_SZ и данные **% systemroot %**, тип:
```
REG ADD HKLM\Software\MyCo /v Path /t REG_EXPAND_SZ /d ^%systemroot^%
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
