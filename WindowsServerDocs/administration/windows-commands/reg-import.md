---
title: reg import
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0be103de-08fc-4f02-b590-361782680b3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7d1dd1b61848671b528c62fd22fe656e14fda7b1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59861845"
---
# <a name="reg-import"></a>reg import



Копирует содержимое файла, содержащего экспортировать разделы реестра, записи и значения в реестр локального компьютера.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
Reg import FileName
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя файла >|Указывает имя и путь к файлу с содержимым, который необходимо скопировать в реестре локального компьютера. Этот файл должен быть создан заранее с помощью **reg export**.|
|/?|Отображает справку по **reg import** в командной строке.|

## <a name="remarks"></a>Примечания

В следующей таблице перечислены возвращаемые значения для **reg import** операции.

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|

## <a name="BKMK_examples"></a>Примеры

Чтобы импортировать записи реестра из файла с именем AppBkUp.reg, введите следующую команду:
```
reg import AppBkUp.reg
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)