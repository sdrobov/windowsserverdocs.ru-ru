---
title: REG сохранить
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b326482b-c8af-467d-a20c-0481eeda3d5c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2a46dfe081421ed727bd7ffeeab364e6c23dd801
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59841085"
---
# <a name="reg-save"></a>REG сохранить



Сохраняет копию указанных подразделов, записей и значения реестра в указанном файле.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
reg save <KeyName> <FileName> [/y]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<KeyName>|Указывает полный путь к разделу. Для указания удаленных компьютеров включают имя компьютера (в формате \\ \\ComputerName\) как часть *KeyName*. Пропуск \\ \\ComputerName\ вызывает операцию по умолчанию на локальном компьютере. *KeyName* должен содержать допустимый корневой раздел. Приведены допустимые корневые ключи для локального компьютера. HKLM, HKCU, HKCR, HKU и HKCC. Если указан удаленный компьютер, являются допустимым корневые ключи: HKLM и HKU.|
|\<Имя файла >|Указывает имя и путь к файлу, который создается. Если путь не указан, используется текущий путь.|
|/y|Перезаписывает существующий файл с именем *FileName* без запроса подтверждения.|
|/?|Отображает справку по **сохранить reg** в командной строке.|

## <a name="remarks-optional-section"></a>"Примечания" \<дополнительный раздел >

-   В следующей таблице перечислены возвращаемые значения для **сохранить reg** операции.

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|
-   Прежде чем изменять записи в реестре, родительский раздел с необходимо сохранить **сохранить reg** операции. Раздел с можно восстановить в случае сбоя редактирования **восстановления reg** операции.

## <a name="BKMK_examples"></a>Примеры

Чтобы сохранить файл с именем AppBkUp.hiv hive MyApp в текущую папку, введите следующую команду:
```
REG SAVE HKLM\Software\MyCo\MyApp AppBkUp.hiv
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)