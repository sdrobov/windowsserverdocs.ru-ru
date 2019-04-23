---
title: Копировать REG
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fe74213-39ec-4b2d-ba3d-086243eac997
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 11cbfce39433ea18632bec16c524da191def2a07
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59867565"
---
# <a name="reg-copy"></a>Копировать REG



Копирует запись реестра в указанном расположении на локальном или удаленном компьютере.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
reg copy <KeyName1> <KeyName2> [/s] [/f]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<KeyName1 >|Указывает полный путь к разделу для копирования. Чтобы указать удаленный компьютер, включают имя компьютера (в формате \\ \\ComputerName\) как часть *KeyName*. Пропуск \\ \\ComputerName\ вызывает операцию по умолчанию на локальном компьютере. *KeyName* должен содержать допустимый корневой раздел. Приведены допустимые корневые ключи для локального компьютера. HKLM, HKCU, HKCR, HKU и HKCC. Если указан удаленный компьютер, являются допустимым корневые ключи: HKLM и HKU.|
|\<KeyName2>|Указывает полный путь к разделу точки назначения. Чтобы указать удаленный компьютер, включают имя компьютера (в формате \\ \\ComputerName\) как часть *KeyName*. Пропуск \\ \\ComputerName\ вызывает операцию по умолчанию на локальном компьютере. *KeyName* должен содержать допустимый корневой раздел. Приведены допустимые корневые ключи для локального компьютера. HKLM, HKCU, HKCR, HKU и HKCC. Если указан удаленный компьютер, являются допустимым корневые ключи: HKLM и HKU.|
|/s|Копирует все разделы и записи заданного раздела.|
|/f|Копирует раздел без запроса подтверждения.|
|/?|Отображает справку по **reg** копирования в командной строке.|

## <a name="remarks"></a>Примечания

-   При копировании раздела реестра не запрашивать подтверждение.
-   В следующей таблице перечислены возвращаемые значения для **копирования reg** операции.

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|

## <a name="BKMK_examples"></a>Примеры

Чтобы скопировать все подразделы и значения раздела MyApp SaveMyApp ключ, введите следующую команду:
```
REG COPY HKLM\Software\MyCo\MyApp HKLM\Software\MyCo\SaveMyApp /s
```
Чтобы скопировать все значения в раздел MyCo на компьютере с именем ЗОДИАКАЛЬНЫЙ ключу MyCo1 на текущем компьютере, введите следующую команду:
```
REG COPY \\ZODIAC\HKLM\Software\MyCo HKLM\Software\MyCo1
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)