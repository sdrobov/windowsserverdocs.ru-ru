---
title: маска
description: Справочная статья по команде Mask, которая удаляет аппаратные теневые копии, импортированные с помощью команды Import.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bf301474-d74a-44e7-9fad-c8a11e7ca3bd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2839fce0a64f187c1445a5f6a4af6c5f0ebc9fb8
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85922106"
---
# <a name="mask"></a>маска

Удаляет аппаратные теневые копии, импортированные с помощью команды **Import** .

## <a name="syntax"></a>Синтаксис

```
mask <shadowsetID>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| шадовсетид | Удаляет теневые копии, принадлежащие указанному ИДЕНТИФИКАТОРу набора теневых копий. |

#### <a name="remarks"></a>Комментарии

- Вместо *шадовсетид*можно использовать существующий псевдоним или переменную среды. Чтобы просмотреть существующие псевдонимы, используйте параметр **Добавить** без параметров.

### <a name="examples"></a>Примеры

Чтобы удалить импортированную теневую копию *% Import_1%*, введите:

```
mask %Import_1%
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)