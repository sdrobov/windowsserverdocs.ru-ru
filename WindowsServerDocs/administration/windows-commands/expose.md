---
title: предоставлять
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 51cc744bc2b61862ed05ca2e7d0aaa8f70d38692
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59886665"
---
# <a name="expose"></a>предоставлять



Предоставляет постоянное теневого копирования как букву диска, общей папки или точки подключения.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
expose <ShadowID> {<Drive:> | <Share> | <MountPoint>}
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Номер_теневой_копии|Указывает идентификатор теневой теневого копирования, которые вы хотите предоставить.|
|\<Диск: >|Предоставляет указанный теневого копирования как букву диска (например, P:).|
|\<Общий ресурс >|Предоставляет указанный теневую копию в общей папке (например, \\ \\ *MachineName*\).|
|\<Точку подключения >|Предоставляет указанный теневой копии в точку подключения (например, C:\shadowcopy\).|

## <a name="remarks"></a>Примечания

-   Вы можете использовать существующий псевдоним или переменную среды, вместо *Номер_теневой_копии*. Используйте **добавить** без параметров, чтобы просмотреть существующие псевдонимы.

## <a name="BKMK_examples"></a>Примеры

Чтобы предоставить постоянные теневого копирования, связанный с переменной среды VSS_SHADOW_1 как диск X, введите следующую команду:
```
expose %vss_shadow_1% x:
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)