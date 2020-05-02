---
title: convert mbr
description: Справочный раздел по команде Convert MBR, который преобразует пустой базовый диск с стилем разделов GPT в базовый диск с стилем разделов основной загрузочной записи (MBR).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a635a4c0-af73-4330-b021-51d483424537
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 178384ff63267c6ca22069f49b980a316b7695aa
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720761"
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
