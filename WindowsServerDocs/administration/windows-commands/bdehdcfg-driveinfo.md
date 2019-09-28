---
title: BdeHdCfg дривеинфо
description: 'Раздел команд Windows для * * BdeHdCfg: дривеинфо * * — отображает букву диска, общий размер, максимальный объем свободного пространства и характеристики секции.'
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f2d065e7-eced-4509-a1a0-ee2521a7f02e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b0f4541bfd71fb7639d18e6e548559ed02918815
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382268"
---
# <a name="bdehdcfg-driveinfo"></a>BdeHdCfg: дривеинфо

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает букву диска, общий размер, максимальный объем свободного пространства и характеристики секции. В списке перечислены только допустимые секции. Нераспределенное место отсутствует в списке, если уже существуют четыре первичных или расширенных раздела. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).
## <a name="syntax"></a>Синтаксис
```
bdehdcfg -driveinfo <DriveLetter>
```
### <a name="parameters"></a>Параметры

|   Параметр   |                  Описание                  |
|---------------|-----------------------------------------------|
| <DriveLetter> | Указывает букву диска, за которой следует двоеточие. |

## <a name="remarks"></a>Примечания
Команда предназначена только для информационных целей и не вносит изменения в диск.
## <a name="BKMK_Examples"></a>Например
В следующем примере отображаются сведения о диске для диска C.
```
bdehdcfg  driveinfo C:
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [bdehdcfg](bdehdcfg.md)
