---
title: Виде
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bf301474-d74a-44e7-9fad-c8a11e7ca3bd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2f0dc83d7d9f7204f56e95c62b7cfad991f539ef
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373710"
---
# <a name="mask"></a>Виде



Удаляет аппаратные теневые копии, импортированные с помощью команды **Import** .

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
mask <ShadowSetID>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|шадовсетид|Удаляет теневые копии, принадлежащие указанному ИДЕНТИФИКАТОРу набора теневых копий.|

## <a name="remarks"></a>Примечания

-   Вместо *шадовсетид*можно использовать существующий псевдоним или переменную среды. Чтобы просмотреть существующие псевдонимы, используйте параметр **Добавить** без параметров.

## <a name="BKMK_examples"></a>Примеров

Чтобы удалить импортированную теневую копию% Import_1%, введите:
```
mask %Import_1%
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)