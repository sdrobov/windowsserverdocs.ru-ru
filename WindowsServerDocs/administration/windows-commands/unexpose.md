---
title: Unexpose
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58dc7d0f-52e9-4587-9487-d3b4c3e52640
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4e10126739ef82b060e271e9b804a77658b5ec82
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392264"
---
# <a name="unexpose"></a>Unexpose



Унекспосес теневую копию, которая была предоставлена с помощью команды **предоставления** . Предоставленная теневая копия может быть задана с помощью идентификатора теневой копии, буквы диска, общего ресурса или точки подключения.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
unexpose {<ShadowID> | <Drive:> | <Share> | <MountPoint>}
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Шадовид >|Унекспосес теневую копию, заданную по заданному ИДЕНТИФИКАТОРу теневой копии.|
|\<диск: >|Унекспосес теневую копию, связанную с заданной буквой диска (например, диск P).|
|\<общий доступ >|Унекспосес теневую копию, связанную с указанной общей папкой (например, \\\\*MachineName*\).|
|\<точка подключения >|Унекспосес. теневую копию, связанную с указанной точкой подключения (например, К:\шадовкопи\).|

## <a name="remarks"></a>Замечания

-   Вместо *шадовид*можно использовать существующий псевдоним или переменную среды. Чтобы просмотреть существующие псевдонимы, используйте параметр **Добавить** без параметров.

## <a name="BKMK_examples"></a>Примеров

Чтобы Unexpose теневую копию, связанную с диском P, введите:
```
unexpose P:
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)