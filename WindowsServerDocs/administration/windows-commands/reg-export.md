---
title: reg export
description: Справочная статья по команде reg export, которая копирует указанные подразделы, записи и значения локального компьютера в файл для перемещения на другие серверы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0ad9526f-1e29-4fa5-9d2d-feaa92f12d7c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4c0cad839569651823e1c1a2bcca3c17c5550c8a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85934647"
---
# <a name="reg-export"></a>reg export

Копирует указанные подразделы, записи и значения локального компьютера в файл для перемещения на другие серверы.

## <a name="syntax"></a>Синтаксис

```
reg export <keyname> <filename> [/y]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
|--|--|
| `<keyname>` | Указывает полный путь к подразделу. Операция экспорта работает только с локальным компьютером. *KeyName* должен содержать допустимый корневой ключ. Допустимые корневые ключи для локального компьютера: **HKLM**, **HKCU**, **HKCR**, **HKU**и **хккк**. Если имя раздела реестра содержит пробел, заключите имя ключа в кавычки. |
| `<filename>` | Указывает имя и путь к файлу, который будет создан во время операции. Файл должен иметь расширение reg. |
| /y | Перезаписывает существующий файл с именем *filename* без запроса подтверждения. |
| /? | Отображение справки в командной строке. |

#### <a name="remarks"></a>Комментарии

- Возвращаемые значения для операции **reg export** :

    | Значение | Описание: |
    |--|--|
    | 0 | Успех |
    | 1 | Failure |

### <a name="examples"></a>Примеры

Чтобы экспортировать содержимое всех подразделов и значений раздела MyApp в файл Аппбкуп. reg, введите:

```
reg export HKLM\Software\MyCo\MyApp AppBkUp.reg
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
