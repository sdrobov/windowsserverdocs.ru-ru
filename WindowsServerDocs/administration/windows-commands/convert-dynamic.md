---
title: преобразовать динамический
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b8fa4b1-850f-4e48-b05f-871c883ea33c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 15c15d14aeb440c5d7862f0a304f223988f52bbe
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379097"
---
# <a name="convert-dynamic"></a>преобразовать динамический



Преобразует базовый диск в динамический диск.

Инструкции по использованию этой команды см. [в разделе Изменение базового диска на динамический диск](https://go.microsoft.com/fwlink/?LinkId=207047) (https://go.microsoft.com/fwlink/?LinkId=207047) ).

## <a name="syntax"></a>Синтаксис

```
convert dynamic [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Все существующие разделы на базовом диске становятся простыми томами.
-   Для выполнения этой операции необходимо выбрать базовый диск. Используйте команду **Выбор диска** , чтобы выбрать базовый диск и переместить фокус на него.

## <a name="BKMK_examples"></a>Примеров

Чтобы преобразовать базовый диск в динамический, введите:
```
convert dynamic
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

