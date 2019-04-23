---
title: Маска
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bf301474-d74a-44e7-9fad-c8a11e7ca3bd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 353e6080d1f6c548bc907b58655f31d0bce6de8b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858025"
---
# <a name="mask"></a>Маска



Удаляет аппаратных теневых копий, которые были импортированы с помощью **импорта** команды.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
mask <ShadowSetID>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|ShadowSetID|Удаляет теневых копий, принадлежащие указанным идентификатором набор теневого копирования.|

## <a name="remarks"></a>Примечания

-   Вы можете использовать существующий псевдоним или переменную среды, вместо *ShadowSetID*. Используйте **добавить** без параметров, чтобы просмотреть существующие псевдонимы.

## <a name="BKMK_examples"></a>Примеры

Чтобы удалить % Import_1% импортированных теневого копирования, введите следующую команду:
```
mask %Import_1%
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)