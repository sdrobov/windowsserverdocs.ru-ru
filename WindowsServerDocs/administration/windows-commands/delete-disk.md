---
title: удалить диск
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 886e84edf80227d42ad77e36aed388b9e853ca62
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378669"
---
# <a name="delete-disk"></a>удалить диск



Удаляет отсутствующий динамический диск из списка дисков.

Инструкции по использованию этой команды см. [в разделе Удаление отсутствующего динамического диска](https://go.microsoft.com/fwlink/?LinkId=207055) (https://go.microsoft.com/fwlink/?LinkId=207055) ).

## <a name="syntax"></a>Синтаксис

```
delete disk [noerr] [override]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|
|крывают|Позволяет программе DiskPart удалять все простые тома на диске. Если диск содержит половину зеркального тома, половина зеркала на диске удаляется. Команда удалить переопределение диска завершается сбоем, если диск входит в том RAID-5.|

## <a name="BKMK_examples"></a>Примеров

Чтобы удалить отсутствующий динамический диск из списка дисков, введите:
```
delete disk
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

