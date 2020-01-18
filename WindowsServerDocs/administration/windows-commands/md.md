---
title: Md
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 3751b185677bfee9d0519b9a617bea1df063c1e7
ms.sourcegitcommit: 51e0b575ef43cd16b2dab2db31c1d416e66eebe8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2020
ms.locfileid: "76259079"
---
# <a name="md"></a>Md



Создает каталог или подкаталог.

> [!NOTE]
> Эта команда аналогична команде **mkdir** .

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
md [<Drive>:]<Path>
mkdir [<Drive>:]<Path>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|> \<диска:|Указывает диск, на котором нужно создать новый каталог.|
|\<путь >|Обязательный. Указывает имя и расположение нового каталога. Максимальная длина любого отдельного пути определяется файловой системой.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания.

Расширения команд, включенные по умолчанию, позволяют использовать одну команду **MD** для создания промежуточных каталогов по указанному пути.

## <a name="BKMK_examples"></a>Примеры

Чтобы создать каталог с именем Directory1 в текущем каталоге, введите:
```
md Directory1
```
Чтобы создать дерево каталогов Таксес\проперти\куррент в корневом каталоге с включенными расширениями команд, введите:
```
md \Taxes\Property\Current
```
Чтобы создать дерево каталогов Таксес\проперти\куррент в корневом каталоге, как в предыдущем примере, но при отключенных расширениях команд введите следующую последовательность команд:
```
md \Taxes
md \Taxes\Property
md \Taxes\Property\Current
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Cmd](cmd.md)