---
title: reg export
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ad9526f-1e29-4fa5-9d2d-feaa92f12d7c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d7aeddb4b069b1baf5b8f7aaea2730a2b25bdad7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889655"
---
# <a name="reg-export"></a>reg export



Копирует указанный подразделов, записей и значения на локальном компьютере в файл для передачи на другие серверы.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
Reg export KeyName FileName [/y]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<KeyName>|Указывает полный путь к разделу. Операции экспорта работает только с локального компьютера. KeyName должен содержать допустимый корневой раздел. Действительный корневой ключи являются: HKLM, HKCU, HKCR, HKU и HKCC.|
|\<Имя файла >|Указывает имя и путь к файлу должен быть создан во время операции. Файл должен иметь расширение .reg.|
|/y|Перезаписывает существующий файл с именем *FileName* без запроса подтверждения.|
|/?|Отображает справку по **reg export** в командной строке.|

## <a name="remarks"></a>Примечания

В следующей таблице перечислены возвращаемые значения для **reg export** операции.

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|

## <a name="BKMK_examples"></a>Примеры

Чтобы экспортировать содержимое все подразделы и значения ключа MyApp AppBkUp.reg файл, введите следующую команду:
```
reg export HKLM\Software\MyCo\MyApp AppBkUp.reg
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)