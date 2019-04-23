---
title: REG нагрузки
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b0b2b1b-f510-4108-9e9d-7057e924aa6e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ebc75ad78b7334f4d48a085f6870a443b31fa2a9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852195"
---
# <a name="reg-load"></a>REG нагрузки



Записывает сохраненные разделы и записи в другой раздел в реестре. Предназначено для обработки временных файлов, которые используются для устранения неполадок или редактирования реестра.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
reg load KeyName FileName
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<KeyName>|Указывает полный путь к разделу для загрузки. Для указания удаленных компьютеров включают имя компьютера (в формате \\ \\ComputerName\) как часть *KeyName*. Пропуск \\ \\ComputerName\ вызывает операцию по умолчанию на локальном компьютере. *KeyName* должен содержать допустимый корневой раздел. Приведены допустимые корневые ключи для локального компьютера. HKLM, HKCU, HKCR, HKU и HKCC. Если указан удаленный компьютер, являются допустимым корневые ключи: HKLM и HKU.|
|\<Имя файла >|Указывает имя и путь к загружаемому файлу. Этот файл должен быть создан заранее с помощью **сохранить reg** операции и расширение .hiv.|
|/?|Отображает справку по **нагрузки reg** в командной строке.|

## <a name="remarks"></a>Примечания

В следующей таблице перечислены возвращаемые значения для **нагрузки reg** операции.

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|

## <a name="BKMK_examples"></a>Примеры

Чтобы загрузить файл с именем TempHive.hiv для значения ключа, введите:
```
REG LOAD HKLM\TempHive TempHive.hiv
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)