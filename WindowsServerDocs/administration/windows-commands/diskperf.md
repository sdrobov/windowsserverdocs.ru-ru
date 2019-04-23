---
title: diskperf
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f06916e8-069b-4ec8-a6eb-59f1d9f77111
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a99f18b56c9295e902a3c89e2e89b36c9c1b6c89
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852585"
---
# <a name="diskperf"></a>diskperf



В Windows 2000 счетчики производительности физических и логических дисков не включены по умолчанию.

**Diskperf** включается в Windows XP, Windows Server 2003, Windows Server 2008, Windows Vista, Windows Server 2008 R2 и Windows 7, чтобы его можно использовать удаленно включить или отключить счетчики производительности физического или логического диска на компьютерах под управлением Windows 2000.

## <a name="syntax"></a>Синтаксис

```
diskperf [-Y[D|V] | -N[D|V]] [\\computername]
```

## <a name="options"></a>Параметры

|Параметр|Описание|
|------|-----------|
|-?|Отображение контекстной справки.|
|-Y|Запустите все счетчики производительности, после перезагрузки компьютера.|
|-YD|Включите счетчики производительности для физических дисков при перезагрузке компьютера.|
|-YV|Включите счетчики производительности логических дисков или томов хранения данных при перезагрузке компьютера.|
|-N|Отключите все счетчики производительности, после перезагрузки компьютера.|
|-ND|Отключите счетчики производительности для физических дисков при перезагрузке компьютера.|
|-NV|Отключите счетчики производительности логических дисков или томов хранения данных при перезагрузке компьютера.|
|\\\\*\<имя_компьютера >*|Укажите имя компьютера, где вы хотите включить или отключить счетчики производительности.|