---
title: md
description: Справочная статья по команде MD, которая создает каталог или подкаталог.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 82162d00-cc34-4776-9e55-4b4836dbd6a9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e7d5dac14572bfe53f92333cddcdc68bfa0aab1a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85922092"
---
# <a name="md"></a>md

Создает каталог или подкаталог. Расширения команд, включенные по умолчанию, позволяют использовать одну команду **MD** для создания промежуточных каталогов по указанному пути.

> [!NOTE]
> Эта команда аналогична [команде Mkdir](mkdir.md).

## <a name="syntax"></a>Синтаксис

```
md [<drive>:]<path>
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
md Directory1
```

Чтобы создать дерево каталогов *таксес\проперти\куррент* в корневом каталоге с включенными расширениями команд, введите:

```
md \Taxes\Property\Current
```

Чтобы создать дерево каталогов *таксес\проперти\куррент* в корневом каталоге, как в предыдущем примере, но при отключенных расширениях команд введите следующую последовательность команд:

```
md \Taxes
md \Taxes\Property
md \Taxes\Property\Current
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда mkdir](mkdir.md)