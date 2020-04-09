---
title: Md
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 82162d00-cc34-4776-9e55-4b4836dbd6a9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e2fad89fe4b7e8425064301f6020fefaa5705b25
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839587"
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

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|> \<диска:|Указывает диск, на котором нужно создать новый каталог.|
|\<путь >|Обязательное. Указывает имя и расположение нового каталога. Максимальная длина любого отдельного пути определяется файловой системой.|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

Расширения команд, включенные по умолчанию, позволяют использовать одну команду **MD** для создания промежуточных каталогов по указанному пути.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

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

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Cmd](cmd.md)