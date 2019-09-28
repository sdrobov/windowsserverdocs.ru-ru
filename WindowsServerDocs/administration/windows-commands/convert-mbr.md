---
title: convert mbr
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a635a4c0-af73-4330-b021-51d483424537
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 47001415158b3bdb0b06af9114b995a6f0634da1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379074"
---
# <a name="convert-mbr"></a>convert mbr



Преобразует пустой базовый диск со стилем разделов GPT в базовый диск с стилем разделов основной загрузочной записи (MBR).

> [!IMPORTANT]
> Диск должен быть пустым, чтобы преобразовать его в MBR-диск. Создайте резервную копию данных, а затем удалите все разделы или тома перед преобразованием диска.

Инструкции по использованию этой команды см. [в разделе Изменение диска с таблицей разделов GUID на диск главной загрузочной записи](https://go.microsoft.com/fwlink/?LinkId=207050) (https://go.microsoft.com/fwlink/?LinkId=207050) ).

## <a name="syntax"></a>Синтаксис

```
convert mbr [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Для выполнения этой операции необходимо выбрать базовый диск. Используйте команду **Выбор диска** , чтобы выбрать базовый диск и переместить фокус на него.

## <a name="BKMK_examples"></a>Примеров

Чтобы преобразовать базовый диск из стиля раздела GPT в стиль раздела MBR, введите >:
```
convert mbr
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

