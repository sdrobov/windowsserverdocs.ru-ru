---
title: bdehdcfg driveinfo
description: Справочная статья по команде BdeHdCfg дривеинфо, которая отображает букву диска, общий размер, максимальный объем свободного пространства и характеристики секции.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f2d065e7-eced-4509-a1a0-ee2521a7f02e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0063c73cd20aca8c8fe5cc21b245517475268c64
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923486"
---
# <a name="bdehdcfg-driveinfo"></a>BdeHdCfg: дривеинфо

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает букву диска, общий размер, максимальный объем свободного пространства и характеристики секции. В списке перечислены только допустимые секции. Нераспределенное место отсутствует в списке, если уже существуют четыре первичных или расширенных раздела.

>[!NOTE]
> Эта команда предназначена только для информационных целей и не вносит изменения на диск.

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -driveinfo <drive_letter>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| <drive_letter> | Указывает букву диска, за которой следует двоеточие. |

## <a name="example"></a>Пример

Чтобы отобразить сведения о диске диска C:

```
bdehdcfg  driveinfo C:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
