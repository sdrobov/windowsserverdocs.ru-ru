---
title: mkdir
description: Справочный раздел по команде mkdir, который создает каталог или подкаталог.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 033a57a2-5deb-4c98-aa78-61ce8df2a330
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 921e369cb1550bca8e26cc0beada4c1f5c1c3d5b
ms.sourcegitcommit: 5e313a004663adb54c90962cfdad9ae889246151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84354604"
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