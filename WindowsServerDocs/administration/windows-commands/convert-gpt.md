---
title: convert gpt
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3b1b747-0a7a-4be2-8487-2c4be16ee190
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9a6392cbcff618c642b9d0f168fe555e8be9e759
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379091"
---
# <a name="convert-gpt"></a>convert gpt



Преобразует пустой базовый диск с стилем разделов основной загрузочной записи (MBR) в базовый диск с стилем разделов GPT.

Инструкции по использованию этой команды см. в разделе [Изменение диска основной загрузочной записи на диск с таблицей разделов GUID](https://go.microsoft.com/fwlink/?LinkId=207049) (https://go.microsoft.com/fwlink/?LinkId=207049) ).

## <a name="syntax"></a>Синтаксис

```
convert gpt [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

> [!IMPORTANT]
> Чтобы преобразовать диск в GPT-диск, он должен быть пустым. Создайте резервную копию данных, а затем удалите все разделы или тома перед преобразованием диска.
> -   Необходимый минимальный размер диска для преобразования в GPT составляет 128 МБ.
> -   Для выполнения этой операции необходимо выбрать базовый MBR-диск. Используйте команду **Выбор диска** , чтобы выбрать базовый диск и переместить фокус на него.

## <a name="BKMK_examples"></a>Примеров

Чтобы преобразовать базовый диск из стиля раздела MBR в стиль раздела GPT, введите:
```
convert gpt
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

