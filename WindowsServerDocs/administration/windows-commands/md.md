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
ms.openlocfilehash: 965a5c506535a2c52d6cc7b3557c6104182c12a5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373687"
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
|@no__t 0Drive >:|Указывает диск, на котором нужно создать новый каталог.|
|@no__t 0Path >|Обязательный. Указывает имя и расположение нового каталога. Максимальная длина любого отдельного пути определяется файловой системой.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Расширения команд, включенные по умолчанию, позволяют использовать одну команду **MD** для создания промежуточных каталогов по указанному пути.

## <a name="BKMK_examples"></a>Примеров

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
cd \Taxes 
md Property
cd Property
md Current
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Cmd](cmd.md)