---
title: BdeHdCfg дривеинфо
description: Раздел команд Windows для **BdeHdCfg дривеинфо**, который отображает букву диска, общий размер, максимальный объем свободного пространства и характеристики секции.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f2d065e7-eced-4509-a1a0-ee2521a7f02e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9c598ea2d1d140090d623b3b48dbcc1be51ee66c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851067"
---
# <a name="bdehdcfg-driveinfo"></a>BdeHdCfg: дривеинфо

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает букву диска, общий размер, максимальный объем свободного пространства и характеристики секции. В списке перечислены только допустимые секции. Нераспределенное место отсутствует в списке, если уже существуют четыре первичных или расширенных раздела.

Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -driveinfo <DriveLetter>
```

#### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| <DriveLetter> | Указывает букву диска, за которой следует двоеточие. |

## <a name="remarks"></a>Примечания

Команда предназначена только для информационных целей и не вносит изменения в диск.

## <a name="example"></a><a name=BKMK_Examples></a>Например

В следующем примере отображаются сведения о диске для диска C.

```
bdehdcfg  driveinfo C:
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
