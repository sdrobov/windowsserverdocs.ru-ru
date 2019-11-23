---
title: reg export
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 7fb3a779ffe5a4e7d513ca9a3afed8ee90901688
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384748"
---
# <a name="reg-export"></a>reg export



Копирует указанные подразделы, записи и значения локального компьютера в файл для перемещения на другие серверы.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
Reg export KeyName FileName [/y]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<KeyName >|Указывает полный путь к подразделу. Операция экспорта работает только с локальным компьютером. KeyName должен содержать допустимый корневой ключ. Допустимые корневые ключи: HKLM, HKCU, HKCR, HKU и ХККК.|
|\<имя файла >|Указывает имя и путь к файлу, который будет создан во время операции. Файл должен иметь расширение reg.|
|/y|Перезаписывает существующий файл с именем *filename* без запроса подтверждения.|
|/?|Отображает справку по **экспорту реестра** в командной строке.|

## <a name="remarks"></a>Замечания

В следующей таблице перечислены возвращаемые значения для операции **reg export** .

|Значение|Описание|
|-----|-----------|
|0|Выполнено|
|1|Сбой|

## <a name="BKMK_examples"></a>Примеров

Чтобы экспортировать содержимое всех подразделов и значений раздела MyApp в файл Аппбкуп. reg, введите:
```
reg export HKLM\Software\MyCo\MyApp AppBkUp.reg
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)