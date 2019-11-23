---
title: справка
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c65b5ac3-711a-4368-95b8-ba82e2d00713
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1d759c85c07d76811053ba0a4a938e07220c2648
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375595"
---
# <a name="help"></a>справка



Предоставляет оперативную информацию о системных командах (то есть командах, отличных от сетевых). Если используется без параметров, **Справочные** списки и краткое описание каждой системной команды.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
help [<Command>] 
[<Command>] /?
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Команда \<>|Указывает имя команды, сведения о которой требуется получить.|

## <a name="BKMK_examples"></a>Примеров

Чтобы просмотреть сведения о команде **Robocopy** , введите одно из следующих действий:
```
help robocopy
robocopy /? 
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)