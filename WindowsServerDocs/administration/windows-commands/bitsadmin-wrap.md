---
title: bitsadmin wrap
description: Раздел команд Windows для **битсадмин** . заключает в оболочку любую строку выходного текста, выходящий за пределы крайнего правого края окна команд, на следующую строку.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14e57522-539d-4621-ad15-09f7a44ccab7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5609fb6f38716795a545e0c7fe3939f893a8c8d5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380677"
---
# <a name="bitsadmin-wrap"></a>bitsadmin wrap

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Заключает выходные данные в командное окно.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Wrap Job
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Укажите перед другими параметрами. По умолчанию все параметры, кроме коммутатора [монитора битсадмин](bitsadmin-monitor.md) , заключают выходные данные в оболочку.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекаются сведения о задании с именем *мидовнлоаджоб* и переносятся выходные данные.

```
C:\>bitsadmin /Wrap /Info myDownloadJob /verbose
```

#### <a name="additional-references"></a>Дополнительные ссылки

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
