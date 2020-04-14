---
title: Задать контекст
description: Раздел команд Windows для Set Context, который задает контекст для создания теневой копии.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fc16c7dd-e8f0-4c2a-8742-0bddb2848bfd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 162fefc46bc3b8ae39dcb41a387e50ed98fefa70
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834567"
---
# <a name="set-contex"></a>Задать контекста

Задает контекст для создания теневой копии. Если используется без параметров, **контекст Set** отображает справку в командной строке.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
set context {clientaccessible | persistent [nowriters] | volatile [nowriters]}
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|клиентакцессибле|Указывает, что теневая копия может использоваться клиентскими версиями Windows.|
|надежно|Указывает, что теневая копия сохраняется по выходу из программы, сбросу или перезапуску.|
|volatile|Удаляет теневую копию при выходе или сбросе.|
|средства записи|Указывает, что все модули записи исключены.|

## <a name="remarks"></a>Примечания

-   По умолчанию контекст *клиентакцессибле* является постоянным.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы предотвратить удаление теневых копий при выходе из сценария DiskShadow, введите:
```
set context persistent
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)