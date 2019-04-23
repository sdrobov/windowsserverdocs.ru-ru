---
title: reg unload
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: aaa7d7a9fa82db2968d988e3b7b3fb8275a72337
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59834985"
---
# <a name="reg-unload"></a>reg unload



Удаляет раздел реестра, который был загружен с помощью **нагрузки reg** операции.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
reg unload <KeyName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<KeyName>|Указывает полный путь к разделу для выгрузки. Для указания удаленных компьютеров включают имя компьютера (в формате \\ \\ComputerName\) как часть *KeyName*. Пропуск \\ \\ComputerName\ вызывает операцию по умолчанию на локальном компьютере. *KeyName* должен содержать допустимый корневой раздел. HKLM, HKCU, HKCR, HKU и HKCC допустимым корневые ключи для локального компьютера: Если указан удаленный компьютер, допустимым корневые ключи являются HKLM и HKU.|
|/?|Отображает справку по **reg unload** в командной строке.|

## <a name="remarks"></a>Примечания

В следующей таблице перечислены возвращаемые значения для **reg unload** параметр.

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|

## <a name="BKMK_examples"></a>Примеры

Чтобы выгрузить куст TempHive в файле HKLM, введите:
```
REG UNLOAD HKLM\TempHive
```

> [!CAUTION]
> Не изменять реестр напрямую, если нет других возможностей. Редактор реестра обходит стандартную защиту, настраивая параметры, которые могут привести к снижению производительности, повредить систему или даже потребуется переустановить Windows. Большинство параметров реестра можно безопасно изменить с помощью программ в панели управления или консоли управления (MMC). Если необходимо изменить реестр напрямую, сделайте резервную копию.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)