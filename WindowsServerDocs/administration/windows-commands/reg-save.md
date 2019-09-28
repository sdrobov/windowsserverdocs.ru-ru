---
title: сохранить reg
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 6ae07cd3c90c51e7bd494bc6c35919680cde912a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371705"
---
# <a name="reg-save"></a>сохранить reg



Сохраняет копию указанных подразделов, записей и значений реестра в указанном файле.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
reg save <KeyName> <FileName> [/y]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0KeyName >|Указывает полный путь к подразделу. Для указания удаленных компьютеров включите имя компьютера (в формате \\ @ no__t-1ComputerName @ no__t-2 в составе *keyName*. Пропуск \\ @ no__t-1ComputerName \ приводит к тому, что по умолчанию операция выполняется на локальном компьютере. *KeyName* должен содержать допустимый корневой ключ. Допустимые корневые ключи для локального компьютера: HKLM, HKCU, HKCR, HKU и ХККК. Если указан удаленный компьютер, допустимые корневые ключи: HKLM и HKU.|
|\<Имя файла >|Указывает имя и путь к создаваемому файлу. Если путь не указан, используется текущий путь.|
|/y|Перезаписывает существующий файл с именем *filename* без запроса подтверждения.|
|/?|Отображает справку по **сохранению reg** в командной строке.|

## <a name="remarks-optional-section"></a>Примечания \<optional раздела >

-   В следующей таблице перечислены возвращаемые значения для операции **reg save** .

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|
-   Перед тем как вносить изменения в записи реестра, сохраните родительский подраздел с операцией **reg save** . Если операция изменения не удалась, восстановите исходный подраздел с операцией **восстановления reg** .

## <a name="BKMK_examples"></a>Примеров

Чтобы сохранить Hive MyApp в текущей папке в виде файла с именем Аппбкуп. ВИЧ, введите:
```
REG SAVE HKLM\Software\MyCo\MyApp AppBkUp.hiv
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)