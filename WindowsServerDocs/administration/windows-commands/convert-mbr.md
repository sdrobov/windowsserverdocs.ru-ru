---
title: convert mbr
description: Раздел команд Windows для преобразования MBR, который преобразует пустой базовый диск с стилем разделов GPT в базовый диск с стилем разделов основной загрузочной записи (MBR).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a635a4c0-af73-4330-b021-51d483424537
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: eeaf79a380fb5f1074d2bbef004537804caa0d8d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847207"
---
# <a name="convert-mbr"></a>convert mbr

Преобразует пустой базовый диск со стилем разделов GPT в базовый диск с стилем разделов основной загрузочной записи (MBR).

> [!IMPORTANT]
> Диск должен быть пустым, чтобы преобразовать его в MBR-диск. Создайте резервную копию данных, а затем удалите все разделы или тома перед преобразованием диска.

Инструкции по использованию этой команды см. [в разделе Изменение диска с таблицей разделов GUID на диск главной загрузочной записи](https://go.microsoft.com/fwlink/?LinkId=207050) (https://go.microsoft.com/fwlink/?LinkId=207050).

## <a name="syntax"></a>Синтаксис

```
convert mbr [noerr]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Для выполнения этой операции необходимо выбрать базовый диск. Используйте команду **Выбор диска** , чтобы выбрать базовый диск и переместить фокус на него.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы преобразовать базовый диск из стиля раздела GPT в стиль раздела MBR, введите >:
```
convert mbr
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

