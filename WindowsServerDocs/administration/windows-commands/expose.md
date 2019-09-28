---
title: представлены
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b0a21cf-3bef-4ade-b8f1-ac42f9203947
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 819484364e8375c4d58e4d022681eedeaa7084ab
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377278"
---
# <a name="expose"></a>представлены



Предоставляет постоянную теневую копию в виде буквы диска, общего ресурса или точки подключения.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
expose <ShadowID> {<Drive:> | <Share> | <MountPoint>}
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|шадовид|Указывает теневой идентификатор теневой копии, которую необходимо предоставить.|
|\<Drive: >|Предоставляет указанную теневую копию в виде буквы диска (например, P:).|
|@no__t 0Share >|Предоставляет указанную теневую копию в общей папке (например, \\ @ no__t-1*MachineName*\)).|
|@no__t 0MountPoint >|Предоставляет указанную теневую копию точке подключения (например, К:\шадовкопи @ no__t-0).|

## <a name="remarks"></a>Примечания

-   Вместо *шадовид*можно использовать существующий псевдоним или переменную среды. Чтобы просмотреть существующие псевдонимы, используйте параметр **Добавить** без параметров.

## <a name="BKMK_examples"></a>Примеров

Чтобы предоставить устойчивую теневую копию, связанную с переменной среды VSS_SHADOW_1, в качестве диска X, введите:
```
expose %vss_shadow_1% x:
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)