---
title: bitsadmin suspend
description: Раздел Windows команды для **bitsadmin приостановить** -приостанавливает работу указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 87e1bbd1b068d68fb60655043735c6c1aeb07707
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825925"
---
# <a name="bitsadmin-suspend"></a>bitsadmin suspend

> Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Приостанавливает работу указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Suspend <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Чтобы перезапустить задание, используйте [bitsadmin resume](bitsadmin-resume.md) переключения.

## <a name="BKMK_examples"></a>Примеры

Следующий пример приостанавливает задание с именем *myDownloadJob*.

```
C:\>bitsadmin /Suspend myDownloadJob
```

#### <a name="additional-references"></a>Дополнительные ссылки

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
