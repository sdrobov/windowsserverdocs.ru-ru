---
title: bitsadmin suspend
description: Раздел команд Windows для битсадмин Suspend, который приостанавливает указанное задание.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f9d42500-7bea-4aa8-a9f0-c22f6ed3e73b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0419f4cdf59d04539b8b4c6d47cec886197d412b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849057"
---
# <a name="bitsadmin-suspend"></a>bitsadmin suspend

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Приостанавливает указанное задание.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Suspend <Job>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Чтобы перезапустить задание, используйте параметр [возобновления битсадмин](bitsadmin-resume.md) .

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере приостанавливается задание с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /Suspend myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
