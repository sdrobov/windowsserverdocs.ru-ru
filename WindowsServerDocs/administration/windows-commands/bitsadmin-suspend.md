---
title: bitsadmin suspend
description: Раздел команд Windows для **битсадмин Suspend** — приостановка указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f9d42500-7bea-4aa8-a9f0-c22f6ed3e73b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7a3a484df2b50cdc8893512020b835f913793d2c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380378"
---
# <a name="bitsadmin-suspend"></a>bitsadmin suspend

> Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Приостанавливает указанное задание.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Suspend <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Чтобы перезапустить задание, используйте параметр [возобновления битсадмин](bitsadmin-resume.md) .

## <a name="BKMK_examples"></a>Примеров

В следующем примере приостанавливается задание с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /Suspend myDownloadJob
```

#### <a name="additional-references"></a>Дополнительные ссылки

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
