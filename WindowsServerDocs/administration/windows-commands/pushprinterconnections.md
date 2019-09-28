---
title: pushprinterconnections
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c30afb97-b149-478f-a4b9-2cbc25361818 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fe25a29af34f78ebe161dc0d07c5edf64257f5c2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371960"
---
# <a name="pushprinterconnections"></a>pushprinterconnections



Считывает развернутые параметры подключения принтера из групповая политика и развертывает и удаляет подключения принтеров по мере необходимости.

## <a name="syntax"></a>Синтаксис

```
pushprinterconnections <-log> <-?>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|> < журнала|Записывает файл журнала отладки на пользователя в% TEMP или записывает журнал отладки на компьютер в%виндир%\темп.|
|<-? >|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

Эта служебная программа предназначена для использования при запуске компьютера или в сценариях входа пользователя в систему и не должна запускаться из командной строки.

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Развертывание принтеров с помощью групповая политика](https://go.microsoft.com/fwlink/?LinkId=230627)