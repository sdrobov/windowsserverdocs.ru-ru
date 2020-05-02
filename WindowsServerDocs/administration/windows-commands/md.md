---
title: Md
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 82162d00-cc34-4776-9e55-4b4836dbd6a9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a605571fb74af99d0f365a100dd33fd4db0d3f22
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724008"
---
# <a name="md"></a>Md



Создает каталог или подкаталог.

> [!NOTE]
> Эта команда аналогична команде **mkdir** .



## <a name="syntax"></a>Синтаксис

```
md [<Drive>:]<Path>
mkdir [<Drive>:]<Path>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<> диска:|Указывает диск, на котором нужно создать новый каталог.|
|\<> пути|Обязательный. Указывает имя и расположение нового каталога. Максимальная длина любого отдельного пути определяется файловой системой.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Расширения команд, включенные по умолчанию, позволяют использовать одну команду **MD** для создания промежуточных каталогов по указанному пути.

## <a name="examples"></a>Примеры

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

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Cmd](cmd.md)