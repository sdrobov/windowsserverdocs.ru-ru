---
title: mkdir
description: Справочная статья по команде mkdir, которая создает каталог или подкаталог.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 033a57a2-5deb-4c98-aa78-61ce8df2a330
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c7c1569e82143443de861216e40b904de4481a03
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931287"
---
# <a name="mkdir"></a>mkdir

Создает каталог или подкаталог. Расширения команд, включенные по умолчанию, позволяют использовать одну команду **mkdir** для создания промежуточных каталогов по указанному пути.

> [!NOTE]
> Эта команда аналогична [команде MD](md.md).

## <a name="syntax"></a>Синтаксис

```
mkdir [<drive>:]<path>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<drive>`: | Указывает диск, на котором нужно создать новый каталог. |
| `<path>` | Указывает имя и расположение нового каталога. Максимальная длина любого отдельного пути определяется файловой системой. Это обязательный параметр. |
| /? | Отображение справки в командной строке. |

### <a name="examples"></a>Примеры

Чтобы создать каталог с именем *Directory1* в текущем каталоге, введите:

```
mkdir Directory1
```

Чтобы создать дерево каталогов *таксес\проперти\куррент* в корневом каталоге с включенными расширениями команд, введите:

```
mkdir \Taxes\Property\Current
```

Чтобы создать дерево каталогов *таксес\проперти\куррент* в корневом каталоге, как в предыдущем примере, но при отключенных расширениях команд введите следующую последовательность команд:

```
mkdir \Taxes
mkdir \Taxes\Property
mkdir \Taxes\Property\Current
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [MD, команда](md.md)