---
title: Отключенный том
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b8f7192f-ea38-47d0-9d4e-58ef68336ae6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bd14492a40046472f43f37d79c393c9467fe4a88
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873745"
---
# <a name="offline-volume"></a>Отключенный том



Переводит online том с фокусом в автономный режим.

> [!IMPORTANT]
> Эта команда DiskPart не доступна в любом выпуске Windows Vista.

## <a name="syntax"></a>Синтаксис

```
offline volume [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Для этого необходимо выбрать том. Используйте **выберите том** команду, чтобы выбрать диск и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Чтобы отключить диск, имеющий фокус, введите следующую команду:
```
offline volume
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

