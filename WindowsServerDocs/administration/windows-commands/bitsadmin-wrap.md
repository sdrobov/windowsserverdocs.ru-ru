---
title: bitsadmin wrap
description: Команды Windows для битсадмин Wrap, которая заключает в оболочку любую строку выходного текста, расположенную за крайней правой границей окна команд, до следующей строки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 14e57522-539d-4621-ad15-09f7a44ccab7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 009a0452f44c4944ae110ca6b9e0570793c32a72
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848757"
---
# <a name="bitsadmin-wrap"></a>bitsadmin wrap

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Заключает строку выходного текста, выходящего за пределы крайнего правого края окна команд, на следующую строку.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Wrap Job
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Укажите перед другими параметрами. По умолчанию все параметры, кроме коммутатора [монитора битсадмин](bitsadmin-monitor.md) , заключают выходные данные в оболочку.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекаются сведения о задании с именем *мидовнлоаджоб* и переносятся выходные данные.

```
C:\>bitsadmin /Wrap /Info myDownloadJob /verbose
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
