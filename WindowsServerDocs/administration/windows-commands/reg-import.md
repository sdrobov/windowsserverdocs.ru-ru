---
title: reg import
description: Справочная статья по команде reg import, которая копирует содержимое файла, содержащего экспортированные подразделы, записи и значения реестра, в реестр локального компьютера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0be103de-08fc-4f02-b590-361782680b3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 77c8284dd2341f37292afdfd810b2182686aad68
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931867"
---
# <a name="reg-import"></a>reg import

Копирует содержимое файла, содержащего экспортированные подразделы, записи и значения реестра, в реестр локального компьютера.

## <a name="syntax"></a>Синтаксис

```
reg import <filename>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
|--|--|
| `<filename>` | Указывает имя и путь к файлу, который содержит содержимое, копируемое в реестр локального компьютера. Этот файл должен быть создан заранее с помощью команды **reg export**. |
| /? | Отображение справки в командной строке. |

#### <a name="remarks"></a>Комментарии

- Возвращаемые значения для операции **reg import** :

    | Значение | Описание: |
    |--|--|
    | 0 | Успех |
    | 1 | Failure |

### <a name="examples"></a>Примеры

Чтобы импортировать записи реестра из файла с именем Аппбкуп. reg, введите:

```
reg import AppBkUp.reg
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда Reg Export](reg-export.md)
