---
title: добавить псевдоним
description: Раздел Windows команды для **добавить псевдоним** -добавляет псевдонимы среды псевдоним.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 50de932ea0153546816face61f0852a08707ea85
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862225"
---
# <a name="add-alias"></a>добавить псевдоним



Добавляет псевдонимы среды псевдоним. При использовании без параметров, **добавить псевдоним** отображает справку в командной строке.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
add alias <AliasName> <AliasValue>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<AliasName>|Задает имя псевдонима.|
|\<AliasValue>|Указывает значение псевдонима.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Псевдонимы, сохраняются в файле метаданных и они будут загружены с **загрузить метаданные** команды.

## <a name="BKMK_examples"></a>Примеры

Чтобы получить список всех теней, включая их псевдонимов, введите следующую команду:
```
list shadows all
```
В следующем фрагменте представлен теневого копирования, которой назначен псевдоним по умолчанию, VSS_SHADOW_x:
```
* Shadow Copy ID = {ff47165a-1946-4a0c-b7f4-80f46a309278}
%VSS_SHADOW_1%
```
Чтобы назначить новый псевдоним с именем System1 этой теневой копии, введите следующую команду:
```
add alias System1 %VSS_SHADOW_1%
```
Кроме того можно будет назначить псевдоним с помощью идентификатора теневой копии.
```
add alias System1 {ff47165a-1946-4a0c-b7f4-80f46a309278}
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)