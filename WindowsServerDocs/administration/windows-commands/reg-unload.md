---
title: reg unload
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d07791d-ca27-454e-9797-27d7e84c5048
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 32df397b597291269dcfb1449d00e86b2f4f5836
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384617"
---
# <a name="reg-unload"></a>reg unload



Удаляет раздел реестра, который был загружен с помощью операции **загрузки reg** .

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
reg unload <KeyName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0KeyName >|Указывает полный путь к подразделу, который нужно выгрузить. Для указания удаленных компьютеров включите имя компьютера (в формате \\ @ no__t-1ComputerName @ no__t-2 в составе *keyName*. Пропуск \\ @ no__t-1ComputerName \ приводит к тому, что по умолчанию операция выполняется на локальном компьютере. *KeyName* должен содержать допустимый корневой ключ. Допустимые корневые ключи для локального компьютера: HKLM, HKCU, HKCR, HKU и ХККК. Если указан удаленный компьютер, допустимыми корневыми ключами являются HKLM и HKU.|
|/?|Отображает справку для **reg unload** в командной строке.|

## <a name="remarks"></a>Примечания

В следующей таблице перечислены возвращаемые значения для параметра **reg unload** .

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|

## <a name="BKMK_examples"></a>Примеров

Чтобы выгрузить Темфиве Hive в файле HKLM, введите:
```
REG UNLOAD HKLM\TempHive
```

> [!CAUTION]
> Не изменяйте реестр напрямую, если нет альтернативы. Редактор реестра обходит стандартные средства защиты, что позволяет снизить производительность, повредить систему или даже потребовать переустановки Windows. Большинство параметров реестра можно безопасно изменить с помощью программы на панели управления или консоли управления (MMC). Если необходимо непосредственно изменить реестр, сначала создайте его резервную копию.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)