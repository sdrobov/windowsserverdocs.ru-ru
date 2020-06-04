---
title: маска
description: Справочный раздел по команде Mask, который удаляет аппаратные теневые копии, импортированные с помощью команды Import.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bf301474-d74a-44e7-9fad-c8a11e7ca3bd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ee01bb74b1fef1bb31a266c01a9e9bde7743691d
ms.sourcegitcommit: 5e313a004663adb54c90962cfdad9ae889246151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84354644"
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

#### <a name="remarks"></a>Remarks

- Вместо *шадовсетид*можно использовать существующий псевдоним или переменную среды. Чтобы просмотреть существующие псевдонимы, используйте параметр **Добавить** без параметров.

### <a name="examples"></a>Примеры

Чтобы удалить импортированную теневую копию *% Import_1%*, введите:

```
mask %Import_1%
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)