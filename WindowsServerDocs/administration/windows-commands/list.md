---
title: list
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 91b42925fc822b10157bb488167d06fe82cfe1e3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374698"
---
# <a name="list"></a>list



Перечисляет модули записи, теневые копии или зарегистрированные в настоящее время поставщики теневого копирования, которые находятся в системе. Если используется без параметров, **список** отображает справку в командной строке.

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
|средствами|Выводит список модулей записи. Синтаксис и параметры см. в разделе [модули записи списка](list-writers.md) .|
|Темно|Список постоянных и существующих непостоянных теневых копий. Синтаксис и параметры см. в разделе [список теней](list-shadows.md) .|
|поставщик|Перечисляет зарегистрированные в настоящее время поставщики теневого копирования. Синтаксис и параметры см. в разделе [поставщики списков](list-providers.md) .|

## <a name="BKMK_examples"></a>Примеров

Чтобы получить список всех теневых копий, введите:
```
list shadows all
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)