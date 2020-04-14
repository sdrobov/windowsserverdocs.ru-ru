---
title: оперативный том
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5da073fd-578d-4691-ad0f-605ba66e0c7e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 476dd893e7899a2bd58336546a7881934f415f92
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837847"
---
# <a name="online-volume"></a>оперативный том



Переводит тома, находящиеся в режиме «вне сети», в оперативный режим

> [!IMPORTANT]
> Эта команда недоступна ни в одном из выпусков Windows Vista.

> [!IMPORTANT]
> Эта команда завершится ошибкой, если она используется на томе, доступном только для чтения.

## <a name="syntax"></a>Синтаксис

```
online volume [noerr]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Эта команда работает с томами, которые завершились сбоем, завершаются сбоем или находятся в состоянии Отказавшая избыточность.
-   Для завершения этой команды необходимо выбрать том. Используйте команду **выбрать том** , чтобы выбрать том и переместить фокус на него.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы перевести том с фокусом в режим «в сети», введите:
```
online volume
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

