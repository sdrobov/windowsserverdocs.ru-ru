---
title: reg delete
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cee05071-1607-4ab1-b8ab-65caebeb85c3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 369ef3bda37ab8e143a14f0f9707b9bbf14bd5f8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59877085"
---
# <a name="reg-delete"></a>reg delete



Удаляет раздел или записи из реестра.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
Reg delete <KeyName> [{/v ValueName | /ve | /va}] [/f]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<KeyName>|Указывает полный путь к подраздела или записи для удаления. Чтобы указать удаленный компьютер, включают имя компьютера (в формате \\ \\ComputerName\) как часть *KeyName*. Пропуск \\ \\ComputerName\ вызывает операцию по умолчанию на локальном компьютере. *KeyName* должен содержать допустимый корневой раздел. Приведены допустимые корневые ключи для локального компьютера. HKLM, HKCU, HKCR, HKU и HKCC. Если указан удаленный компьютер, являются допустимым корневые ключи: HKLM и HKU.|
|/v \<ValueName>|Удаляет запись в подразделе. Если запись не задана, будут удалены все записи и вложенные разделы данного раздела.|
|/ ve|Указывает, что будут удалены только те записи, которые не имеют значения.|
|/VA|Удаляет все записи заданного раздела. Подразделы в разделе заданный подраздел не удаляются.|
|/f|Удаляет существующий раздел реестра или запись без запроса на подтверждение.|
|/?|Отображает справку по **удалить reg** в командной строке.|

## <a name="remarks"></a>Примечания

В следующей таблице перечислены возвращаемые значения для **удалить reg** операции.

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|

## <a name="BKMK_examples"></a>Примеры

Чтобы удалить раздел реестра время ожидания и все подразделы и значения, введите следующую команду:
```
REG DELETE HKLM\Software\MyCo\MyApp\Timeout
```
Чтобы удалить значение реестра MTU под HKLM\Software\MyCo на компьютере с именем ЗОДИАКАЛЬНЫЙ, введите следующую команду:
```
REG DELETE \\ZODIAC\HKLM\Software\MyCo /v MTU
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)