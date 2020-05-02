---
title: маска
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bf301474-d74a-44e7-9fad-c8a11e7ca3bd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 816bcd932091b33ed897add5a13603e3a1eea925
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724009"
---
# <a name="mask"></a>маска



Удаляет аппаратные теневые копии, импортированные с помощью команды **Import** .



## <a name="syntax"></a>Синтаксис

```
mask <ShadowSetID>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|шадовсетид|Удаляет теневые копии, принадлежащие указанному ИДЕНТИФИКАТОРу набора теневых копий.|

## <a name="remarks"></a>Примечания

-   Вместо *шадовсетид*можно использовать существующий псевдоним или переменную среды. Чтобы просмотреть существующие псевдонимы, используйте параметр **Добавить** без параметров.

## <a name="examples"></a>Примеры

Чтобы удалить импортированную теневую копию% Import_1%, введите:
```
mask %Import_1%
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)