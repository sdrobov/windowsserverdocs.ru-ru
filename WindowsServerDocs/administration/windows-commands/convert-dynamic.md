---
title: convert dynamic
description: Справочная статья по динамической команде Convert, преобразующая базовый диск в динамический диск.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7b8fa4b1-850f-4e48-b05f-871c883ea33c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3474da8c1f4a3e58d9e77c36abe4390ec2f5b731
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928974"
---
# <a name="convert-dynamic"></a>convert dynamic

Преобразует базовый диск в динамический диск. Для выполнения этой операции необходимо выбрать базовый диск. Используйте [команду Выбор диска](select-disk.md) , чтобы выбрать базовый диск и переместить фокус на него.

> [!NOTE]
> Инструкции по использованию этой команды см. в разделе [Переключение динамического диска обратно на базовый диск](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc755238(v=ws.11)).

## <a name="syntax"></a>Синтаксис

```
convert dynamic [noerr]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Noerr | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |

#### <a name="remarks"></a>Комментарии

- Все существующие разделы на базовом диске становятся простыми томами.

## <a name="examples"></a>Примеры

Чтобы преобразовать базовый диск в динамический, введите:

```
convert dynamic
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [преобразовать команду](convert.md)
