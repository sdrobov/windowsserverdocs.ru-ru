---
title: Удалить диск
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44079900-e4ed-49d0-81e4-d652c38cd636
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e401133854118e82a45fd5e01466288ae41f67da
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863915"
---
# <a name="delete-disk"></a>Удалить диск



Удаление отсутствующего динамического диска из списка дисков.

Инструкции о том, как использовать эту команду, см. в разделе [удаление отсутствует динамического диска](https://go.microsoft.com/fwlink/?LinkId=207055) (https://go.microsoft.com/fwlink/?LinkId=207055).

## <a name="syntax"></a>Синтаксис

```
delete disk [noerr] [override]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|
|Переопределение|Позволяет программе DiskPart удалить все простые тома на диске. Если диск содержит половину зеркального тома, удаляется половине зеркало на диске. Команда delete диска переопределение завершается неудачей, если диск является членом тома RAID-5.|

## <a name="BKMK_examples"></a>Примеры

Чтобы удалить отсутствующий динамический диск в списке дисков, введите следующую команду:
```
delete disk
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

