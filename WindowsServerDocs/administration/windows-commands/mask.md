---
title: виде
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bf301474-d74a-44e7-9fad-c8a11e7ca3bd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a1cb92caacb955449c1baaad411fdbe4cdf05b73
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839647"
---
# <a name="mask"></a>виде



Удаляет аппаратные теневые копии, импортированные с помощью команды **Import** .

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

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

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы удалить импортированную теневую копию% Import_1%, введите:
```
mask %Import_1%
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)