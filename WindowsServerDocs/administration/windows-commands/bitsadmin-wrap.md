---
title: bitsadmin wrap
description: Раздел Windows команды для **bitsadmin wrap** -заключает в оболочку любую строку вывода текста, выходящие за пределы правый край окна команд на следующую строку.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 4834a8a17c72394b6ee8f051ec76919af9880124
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59881675"
---
# <a name="bitsadmin-wrap"></a>bitsadmin wrap

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Вывод выходных данных помещается в окно командной строки.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Wrap Job
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Укажите перед другими параметрами. По умолчанию всех коммутаторов, за исключением [bitsadmin монитор](bitsadmin-monitor.md) переключения, поместите выходные данные.

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекаются сведения о задании с именем *myDownloadJob* и помещает выходные данные.

```
C:\>bitsadmin /Wrap /Info myDownloadJob /verbose
```

#### <a name="additional-references"></a>Дополнительные ссылки

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
