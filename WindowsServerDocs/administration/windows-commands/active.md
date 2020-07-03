---
title: active
description: Справочная статья по активной команде, которая на базовых дисках помечает раздел фокусом как активный.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1f25da2e-87fc-4392-a7ee-f38d09b7873c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a5df2f67c087be31190c512be0f6b20d8a1d72cb
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85924143"
---
# <a name="active"></a>active

На базовых дисках раздел помечается как активный. Только секции могут быть помечены как активные. Для выполнения этой операции необходимо выбрать секцию. Используйте команду **Выбор секции** , чтобы выбрать секцию и переместить фокус на нее.

> [!CAUTION]
> DiskPart информирует только основную систему ввода-вывода (BIOS) или интерфейс EFI, что раздел или том является допустимым системным разделом или системным томом, и может содержать файлы запуска операционной системы. DiskPart не проверяет содержимое раздела. Если вы по ошибке пометите раздел как активный и не содержит загрузочных файлов операционной системы, компьютер может не запуститься.

## <a name="syntax"></a>Синтаксис

```
active
```

## <a name="examples"></a>Примеры

Чтобы пометить секцию фокусом в качестве активной секции, введите:

```
active
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда "выбрать секцию"](select-partition.md)
