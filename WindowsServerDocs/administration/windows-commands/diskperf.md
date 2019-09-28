---
title: diskperf
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 829f0284d761e6a5134011fa1dff99646d55fc13
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377809"
---
# <a name="diskperf"></a>diskperf



В Windows 2000 счетчики производительности физических и логических дисков не включены по умолчанию.

**Diskperf** входит в Windows XP, windows Server 2003, windows Server 2008, Windows Vista, windows Server 2008 R2 и Windows 7, что позволяет удаленно включать или отключать счетчики производительности физических или логических дисков на компьютерах под управлением Windows 2000.

## <a name="syntax"></a>Синтаксис

```
diskperf [-Y[D|V] | -N[D|V]] [\\computername]
```

## <a name="options"></a>Параметры

|Параметр|Описание|
|------|-----------|
|-?|Отображает контекстную справку.|
|-Y|Запуск всех счетчиков производительности диска при перезагрузке компьютера.|
|-ИД|Включите счетчики производительности дисков для физических дисков при перезагрузке компьютера.|
|-ИВ|Включите счетчики производительности дисков для логических дисков или томов хранилища при перезагрузке компьютера.|
|-N|Отключить все счетчики производительности диска при перезагрузке компьютера.|
|-ND|Отключение счетчиков производительности дисков для физических дисков при перезагрузке компьютера.|
|-NV|Отключите счетчики производительности дисков для логических дисков или томов хранилища при перезагрузке компьютера.|
|\\ @ no__t-1 *\<computername >*|Укажите имя компьютера, на котором необходимо включить или отключить счетчики производительности диска.|