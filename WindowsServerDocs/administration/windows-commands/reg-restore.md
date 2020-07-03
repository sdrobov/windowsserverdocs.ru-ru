---
title: reg restore
description: Справочная статья по команде reg restore, которая записывает сохраненные разделы и записи обратно в реестр.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a51f1c0c-969b-4b76-930a-c8bb14dea26e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1483fc6998d7b286a81dc3cb1df021afb7e66650
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931040"
---
# <a name="reg-restore"></a>reg restore

Записывает сохраненные разделы и записи обратно в реестр.

## <a name="syntax"></a>Синтаксис

```
reg restore <keyname> <filename>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
|--|--|
| `<keyname>` | Указывает полный путь к восстанавливаемому подразделу. Операция восстановления работает только с локальным компьютером. *KeyName* должен содержать допустимый корневой ключ. Допустимые корневые ключи для локального компьютера: **HKLM**, **HKCU**, **HKCR**, **HKU**и **хккк**. Если имя раздела реестра содержит пробел, заключите имя ключа в кавычки. |
| `<filename>` | Указывает имя и путь к файлу, содержимое которого записывается в реестр. Этот файл должен быть создан заранее с помощью команды **reg save** и должен иметь расширение ВИЧ. |
| /? | Отображение справки в командной строке. |

#### <a name="remarks"></a>Комментарии

- Перед изменением любых записей реестра необходимо сохранить родительский подраздел с помощью команды **reg save** . В случае сбоя изменения можно восстановить исходный подраздел с помощью операции **восстановления reg** .

- Возвращаемые значения для операции **reg restore** :

    | Значение | Описание: |
    |--|--|
    | 0 | Успех |
    | 1 | Failure |

### <a name="examples"></a>Примеры

Чтобы восстановить файл с именем Нтркбкуп. ВИЧ в ключ Хклм\софтваре\микрософт\рескит и перезаписать существующее содержимое ключа, введите:

```
reg restore HKLM\Software\Microsoft\ResKit NTRKBkUp.hiv
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда reg save](reg-save.md)
