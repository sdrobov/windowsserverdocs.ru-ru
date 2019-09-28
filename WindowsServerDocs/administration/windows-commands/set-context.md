---
title: Задать контекст
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 16f71d831f374f495abf2239cb8e694eee69efdf
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370979"
---
# <a name="set-contex"></a>Задать контекста



Задает контекст для создания теневой копии. Если используется без параметров, **контекст Set** отображает справку в командной строке.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
set context {clientaccessible | persistent [nowriters] | volatile [nowriters]}
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|клиентакцессибле|Указывает, что теневая копия может использоваться клиентскими версиями Windows.|
|надежно|Указывает, что теневая копия сохраняется по выходу из программы, сбросу или перезапуску.|
|независимо|Удаляет теневую копию при выходе или сбросе.|
|средства записи|Указывает, что все модули записи исключены.|

## <a name="remarks"></a>Примечания

-   По умолчанию контекст *клиентакцессибле* является постоянным.

## <a name="BKMK_examples"></a>Примеров

Чтобы предотвратить удаление теневых копий при выходе из сценария DiskShadow, введите:
```
set context persistent
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)