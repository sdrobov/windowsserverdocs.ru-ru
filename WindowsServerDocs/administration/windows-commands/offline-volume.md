---
title: автономный том
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b8f7192f-ea38-47d0-9d4e-58ef68336ae6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d17295f3367fed054a7f6a245bae44ea3494a4a8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723453"
---
# <a name="offline-volume"></a>автономный том



Перевод сетевого тома в состояние "вне сети".

> [!IMPORTANT]
> Эта команда DiskPart недоступна ни в одном из выпусков Windows Vista.

## <a name="syntax"></a>Синтаксис

```
offline volume [noerr]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Для этого необходимо выбрать том. Используйте команду **Выбор тома** , чтобы выбрать диск и переместить фокус на него.

## <a name="examples"></a>Примеры

Чтобы перевести диск с фокусом в режим вне сети, введите:
```
offline volume
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

