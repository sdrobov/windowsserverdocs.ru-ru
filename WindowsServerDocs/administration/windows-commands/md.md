---
title: Md
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82162d00-cc34-4776-9e55-4b4836dbd6a9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1396038410ecc5db5a124a1768038c4f8c8bea8c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59820845"
---
# <a name="md"></a>Md



Создает каталога или подкаталога.

> [!NOTE]
> Эта команда совпадает со значением **mkdir** команды.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
md [<Drive>:]<Path>
mkdir [<Drive>:]<Path>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Диск >:|Диск, на котором вы хотите создать новый каталог.|
|\<Путь >|Обязательный. Указывает имя и расположение нового каталога. Максимальная длина пути определяется в файловой системе.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Расширения команд, которые включены по умолчанию, позволяют использовать единую **md** команду, чтобы создать промежуточные каталоги по указанному пути.

## <a name="BKMK_examples"></a>Примеры

Чтобы создать каталог с именем Directory1 в текущем каталоге, введите следующую команду:
```
md Directory1
```
Чтобы создать дерево каталогов Taxes\Property\Current в корневом каталоге с поддержкой расширения команд, введите следующую команду:
```
md \Taxes\Property\Current
```
Чтобы создать дерево каталогов Taxes\Property\Current в корневом каталоге, как показано в предыдущем примере, но с помощью расширения команд отключена, введите следующую последовательность команд:
```
md \Taxes
cd \Taxes 
md Property
cd Property
md Current
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

[cmd](cmd.md)