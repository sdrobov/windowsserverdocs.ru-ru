---
title: Преобразовать в динамический
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 353c1e4558ab2b0c948ec78c0cd87b579c738ec8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59841615"
---
# <a name="convert-dynamic"></a>Преобразовать в динамический



Преобразует базовый диск в динамический диск.

Инструкции о том, как использовать эту команду, см. в разделе [изменить базовый диск в динамический диск](https://go.microsoft.com/fwlink/?LinkId=207047) (https://go.microsoft.com/fwlink/?LinkId=207047).

## <a name="syntax"></a>Синтаксис

```
convert dynamic [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Все существующие разделы на базовом диске становятся простых томов.
-   Для успешного выполнения этой операции необходимо выбрать базовый диск. Используйте **выберите диск** команду, чтобы выбрать базовый диск и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Чтобы преобразовать базовый диск в динамический диск, введите следующую команду:
```
convert dynamic
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

