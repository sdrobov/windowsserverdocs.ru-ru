---
title: delete volume
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f625933d-0f47-409e-93b2-a3e234049a5d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 35b22e1bfc6fbfca8ef7bd29bfe1b7e28d7d35d5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378650"
---
# <a name="delete-volume"></a>delete volume



Удаляет выбранный том.

## <a name="syntax"></a>Синтаксис

```
delete volume [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Невозможно удалить системный том, загрузочный том, а также любой том, содержащий активный файл подкачки или аварийный дамп (дамп памяти).
-   Для выполнения этой операции необходимо выбрать том. Используйте команду **выбрать том** , чтобы выбрать том и переместить фокус на него.

## <a name="BKMK_examples"></a>Примеров

Чтобы удалить том с фокусом, введите:
```
delete volume
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

