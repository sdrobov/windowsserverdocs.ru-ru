---
title: Задать контекст
description: Справочная статья по параметру SET Context, который задает контекст для создания теневой копии.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fc16c7dd-e8f0-4c2a-8742-0bddb2848bfd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 98fb69f84b15a2444d24e4b6515ff9ff665b9aa7
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85937113"
---
# <a name="set-contex"></a>Задать контекста

Задает контекст для создания теневой копии. Если используется без параметров, **контекст Set** отображает справку в командной строке.



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

## <a name="remarks"></a>Комментарии

-   По умолчанию контекст *клиентакцессибле* является постоянным.

## <a name="examples"></a>Примеры

Чтобы предотвратить удаление теневых копий при выходе из сценария DiskShadow, введите:
```
set context persistent
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)