---
title: label
description: Справочная статья по команде Label, которая создает, изменяет или удаляет метку тома (то есть имя) диска.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bbae8bdd-97d4-4566-9118-7c95aa07645f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f8c13285c5dc5030e96d7d334bb65d15f04dff86
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931810"
---
# <a name="label"></a>label

Создает, изменяет или удаляет метку тома (то есть имя) диска. Если используется без параметров, команда **Label** изменяет метку текущего тома или удаляет существующую метку.

## <a name="syntax"></a>Синтаксис

```
label [/mp] [<volume>] [<label>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| /mp | Указывает, что том следует рассматривать как точку подключения или имя тома. |
| `<volume>` | Указывает букву диска (за которой следует двоеточие), точку подключения или имя тома. Если указано имя тома, параметр **/MP** не требуется. |
| `<label>` | Указывает метку для тома. |
| /? | Отображение справки в командной строке. |

## <a name="remarks"></a>Комментарии

- Windows отображает метку тома и серийный номер (если они есть) в составе списка каталогов.

- Длина метки тома NTFS может составлять до 32 символов, включая пробелы. Метки томов NTFS содержат и отображают вариант, который использовался при создании метки.

## <a name="examples"></a>Примеры

Чтобы пометить диск в дисководе A, который содержит сведения о продажах за Июль, введите:

```
label a:sales-july
```

Чтобы просмотреть и удалить текущую метку для диска C, выполните следующие действия.

1. В командной строке введите:

   ```
   label
   ```

   Должны отобразиться выходные данные, аналогичные приведенным ниже.

   ```
   Volume in drive C: is Main Disk
   Volume Serial Number is 6789-ABCD
   Volume label (32 characters, ENTER for none)?
   ```

2. Нажмите клавишу ВВОД. Должен отобразиться следующий запрос:

   ```
   Delete current volume label (Y/N)?
   ```

3. Нажмите клавишу **Y** , чтобы удалить текущую метку, или **N** , если хотите, чтобы она оставалась существующей.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)