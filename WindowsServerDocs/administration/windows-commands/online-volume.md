---
title: том Online
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5da073fd-578d-4691-ad0f-605ba66e0c7e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6bacba1e204f1eee2e3d4772ff9024aedbfc4fed
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882005"
---
# <a name="online-volume"></a>том Online



Переводит тома, которые сейчас недоступна, подключающееся к сети

> [!IMPORTANT]
> Эта команда не доступна в любом выпуске Windows Vista.

> [!IMPORTANT]
> Эта команда завершится ошибкой, если он используется на томе только для чтения.

## <a name="syntax"></a>Синтаксис

```
online volume [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Эта команда работает на томах, которые не удалось, выполняются или находятся в состоянии Отказавшая избыточность.
-   Для успешного выполнения этой команды должен быть выбран том. Используйте **выберите том** команду, чтобы выбрать том и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Чтобы подключить диск с фокусом в Интернете, введите:
```
online volume
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

