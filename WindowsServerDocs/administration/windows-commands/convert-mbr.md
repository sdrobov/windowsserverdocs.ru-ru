---
title: convert mbr
description: Справочная статья по команде Convert MBR, которая преобразует пустой базовый диск с стилем разделов GPT в базовый диск с стилем разделов основной загрузочной записи (MBR).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a635a4c0-af73-4330-b021-51d483424537
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d53d46b5d7f5a06f389fc665d69508122bd679d9
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928942"
---
# <a name="convert-mbr"></a>convert mbr

Преобразует пустой базовый диск со стилем разделов GPT в базовый диск с стилем разделов основной загрузочной записи (MBR). Для выполнения этой операции необходимо выбрать базовый диск. Используйте [команду Выбор диска](select-disk.md) , чтобы выбрать базовый диск и переместить фокус на него.

> [!IMPORTANT]
> Диск должен быть пустым, чтобы преобразовать его в базовый диск. Создайте резервную копию данных, а затем удалите все разделы или тома перед преобразованием диска.

> [!NOTE]
> Инструкции по использованию этой команды см. [в разделе Изменение диска таблицы разделов с таблицей GUID на диск основной загрузочной записи](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725797(v=ws.11)).

## <a name="syntax"></a>Синтаксис

```
convert mbr [noerr]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Noerr | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |

## <a name="examples"></a>Примеры

Чтобы преобразовать базовый диск из стиля раздела GPT в стиль раздела MBR, введите>:

```
convert mbr
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [преобразовать команду](convert.md)
