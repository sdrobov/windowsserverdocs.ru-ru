---
title: добавить псевдоним
description: Раздел команд Windows для **добавления псевдонима** — Добавляет псевдонимы в среду псевдонима.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5fe12f5d-11e9-4f3d-b7f9-40b26c8685e5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f2834376e497f54eadf1d9077e74f9c398202c5a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382825"
---
# <a name="add-alias"></a>добавить псевдоним



Добавляет псевдонимы в среду псевдонима. Если используется без параметров, команда **Добавить псевдоним** отображает справку в командной строке.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
add alias <AliasName> <AliasValue>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<AliasName >|Задает имя псевдонима.|
|\<Алиасвалуе >|Задает значение псевдонима.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Замечания

-   Псевдонимы сохраняются в файле метаданных и загружаются с помощью команды **Load Metadata** .

## <a name="BKMK_examples"></a>Примеров

Чтобы получить список всех теней, включая их псевдонимы, введите:
```
list shadows all
```
В следующем фрагменте показана теневая копия, которой назначен псевдоним по умолчанию VSS_SHADOW_x.
```
* Shadow Copy ID = {ff47165a-1946-4a0c-b7f4-80f46a309278}
%VSS_SHADOW_1%
```
Чтобы назначить новый псевдоним с именем System1 для этой теневой копии, введите:
```
add alias System1 %VSS_SHADOW_1%
```
Кроме того, псевдоним можно назначить с помощью идентификатора теневой копии:
```
add alias System1 {ff47165a-1946-4a0c-b7f4-80f46a309278}
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)