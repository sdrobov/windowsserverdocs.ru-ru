---
title: convert gpt
description: Раздел команд Windows для Convert GPT, который преобразует пустой базовый диск с стилем разделов основной загрузочной записи (MBR) в базовый диск с стилем разделов GPT.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b3b1b747-0a7a-4be2-8487-2c4be16ee190
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3c1ffe61245f7752ccc81d21d513fa00acd7b68b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847287"
---
# <a name="convert-gpt"></a>convert gpt

Преобразует пустой базовый диск с стилем разделов основной загрузочной записи (MBR) в базовый диск с стилем разделов GPT.

Инструкции по использованию этой команды см. в разделе [Изменение диска основной загрузочной записи на диск с таблицей разделов GUID](https://go.microsoft.com/fwlink/?LinkId=207049) (https://go.microsoft.com/fwlink/?LinkId=207049).

## <a name="syntax"></a>Синтаксис

```
convert gpt [noerr]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

> [!IMPORTANT]
> Чтобы преобразовать диск в GPT-диск, он должен быть пустым. Создайте резервную копию данных, а затем удалите все разделы или тома перед преобразованием диска.
> -   Необходимый минимальный размер диска для преобразования в GPT составляет 128 МБ.
> -   Для выполнения этой операции необходимо выбрать базовый MBR-диск. Используйте команду **Выбор диска** , чтобы выбрать базовый диск и переместить фокус на него.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы преобразовать базовый диск из стиля раздела MBR в стиль раздела GPT, введите:
```
convert gpt
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

