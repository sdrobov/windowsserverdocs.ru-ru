---
title: convert gpt
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 433e30efeecec4e4ec51d67c40c14cacf986d12e
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434226"
---
# <a name="convert-gpt"></a>convert gpt



Преобразует пустой базовый диск со стилем разделов основная загрузочная запись (MBR) в базовый диск со стилем разделов (GPT) таблицы разделов GUID.

Инструкции о том, как использовать эту команду, см. в разделе [изменить диск с основной загрузочной записью с GUID разделов таблицы](https://go.microsoft.com/fwlink/?LinkId=207049) (https://go.microsoft.com/fwlink/?LinkId=207049).

## <a name="syntax"></a>Синтаксис

```
convert gpt [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|

## <a name="remarks"></a>Примечания

> [!IMPORTANT]
> Диск должен быть пустым, чтобы преобразовать в GPT-диск. Резервное копирование данных, а затем удалите все разделы или тома перед преобразованием диска.
> -   Требуется минимальный размер диска для преобразования в формат GPT составляет 128 МБ.
> -   Для успешного выполнения этой операции необходимо выбрать базовый диск MBR. Используйте **выберите диск** команду, чтобы выбрать базовый диск и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Чтобы преобразовать базовый диск из стиля раздела MBR стиль раздела GPT, введите следующую команду:
```
convert gpt
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

