---
title: bdehdcfg driveinfo
description: 'Раздел Windows команды для ** bdehdcfg: driveinfo ** — отображает букву диска, общий размер, максимальное свободное пространство и характеристики секции.'
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: b2dd62e34f8205e0b5d395ba759fff4b4937b0ad
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66435041"
---
# <a name="bdehdcfg-driveinfo"></a>Bdehdcfg: driveinfo

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает имя диска, общий размер, максимальное свободное пространство и характеристики секции. Отображаются только допустимые разделы. Если существует четыре секции основной или дополнительный незанятое пространство отсутствует. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).
## <a name="syntax"></a>Синтаксис
```
bdehdcfg -driveinfo <DriveLetter>
```
### <a name="parameters"></a>Параметры

|   Параметр   |                  Описание                  |
|---------------|-----------------------------------------------|
| <DriveLetter> | Указывает букву диска, за которым следует двоеточие. |

## <a name="remarks"></a>Примечания
Команда носит исключительно информационный характер и делает без изменений на диск.
## <a name="BKMK_Examples"></a>Пример
Следующий пример кода отображает сведения о накопителе для диска C.
```
bdehdcfg  driveinfo C:
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [bdehdcfg](bdehdcfg.md)
