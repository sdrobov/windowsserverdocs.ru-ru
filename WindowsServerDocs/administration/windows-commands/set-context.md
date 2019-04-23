---
title: Контекст набора
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc16c7dd-e8f0-4c2a-8742-0bddb2848bfd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6f24e795f2d7c92d462cf822e70e4830b53827e5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59845855"
---
# <a name="set-contex"></a>Набор контекстного



Задает контекст для теневой копии. При использовании без параметров, **контекст набора** отображает справку в командной строке.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
set context {clientaccessible | persistent [nowriters] | volatile [nowriters]}
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|clientaccessible|Указывает, что теневая копия пригодна для использования в клиентских версиях Windows.|
|Постоянные|Указывает, что теневая копия сохраняется по выходе из программы, сброса или перезапуска.|
|volatile|Операции удаления теневой копии на выход из или сброса.|
|NoWriters|Указывает, что все авторы исключаются.|

## <a name="remarks"></a>Примечания

-   *Clientaccessible* контекст является постоянным по умолчанию.

## <a name="BKMK_examples"></a>Примеры

Чтобы предотвратить удаление при выходе из DiskShadow теневые копии, введите:
```
set context persistent
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)