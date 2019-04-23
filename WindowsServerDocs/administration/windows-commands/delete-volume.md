---
title: delete volume
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 6d25ed68077f594c765cf5630648ad52528d8fe3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59872515"
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
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Невозможно удалить системный том, загрузочный том, а также любой том, содержащий активный файл подкачки или аварийный дамп (дамп памяти).
-   Для успешного выполнения этой операции необходимо выбрать том. Используйте **выберите том** команду, чтобы выбрать том и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Чтобы удалить том, имеющий фокус, введите следующую команду:
```
delete volume
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

