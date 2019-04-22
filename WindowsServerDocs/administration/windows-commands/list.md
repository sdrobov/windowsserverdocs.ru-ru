---
title: list
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57b6c8d0-872e-4dba-9715-1db8ab892e98
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: aacc93e1c7a16a7327ddbd17515f19cf41a5b458
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825545"
---
# <a name="list"></a>list



Список модулей записи, теневые копии или поставщиков зарегистрированные на данный момент теневых копий, которые находятся в системе. При использовании без параметров, **списка** отображает справку в командной строке.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
list writers [metadata | detailed | status]
list shadows {all | set <SetID> | id <ShadowID>}
list providers
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|модули записи|Список модулей записи. См. в разделе [List writers](list-writers.md) для синтаксиса и параметров.|
|Shadows|Выводит список постоянных и существующих временных теневых копий. См. в разделе [список теней](list-shadows.md) для синтаксиса и параметров.|
|Поставщики|Списки в настоящее время зарегистрированных поставщиков теневых копий. См. в разделе [вывести список поставщиков](list-providers.md) для синтаксиса и параметров.|

## <a name="BKMK_examples"></a>Примеры

Чтобы перечислить все теневые копии, введите:
```
list shadows all
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)