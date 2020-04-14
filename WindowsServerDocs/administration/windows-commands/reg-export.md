---
title: reg export
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0ad9526f-1e29-4fa5-9d2d-feaa92f12d7c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5901014511fed0c17a641e1ed183ddbf40dd44c8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836497"
---
# <a name="reg-export"></a>reg export



Копирует указанные подразделы, записи и значения локального компьютера в файл для перемещения на другие серверы.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
Reg export KeyName FileName [/y]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<KeyName >|Указывает полный путь к подразделу. Операция экспорта работает только с локальным компьютером. KeyName должен содержать допустимый корневой ключ. Допустимые корневые ключи: HKLM, HKCU, HKCR, HKU и ХККК.|
|\<имя файла >|Указывает имя и путь к файлу, который будет создан во время операции. Файл должен иметь расширение reg.|
|/y|Перезаписывает существующий файл с именем *filename* без запроса подтверждения.|
|/?|Отображает справку по **экспорту реестра** в командной строке.|

## <a name="remarks"></a>Примечания

В следующей таблице перечислены возвращаемые значения для операции **reg export** .

|Значение|Описание|
|-----|-----------|
|0|Выполнено|
|1|Отказ|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы экспортировать содержимое всех подразделов и значений раздела MyApp в файл Аппбкуп. reg, введите:
```
reg export HKLM\Software\MyCo\MyApp AppBkUp.reg
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)