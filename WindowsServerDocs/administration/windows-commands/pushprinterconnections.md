---
title: pushprinterconnections
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c30afb97-b149-478f-a4b9-2cbc25361818 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5941b1eba55ce7524946f3257c093d409ef7d773
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837077"
---
# <a name="pushprinterconnections"></a>pushprinterconnections



Считывает развернутые параметры подключения принтера из групповая политика и развертывает и удаляет подключения принтеров по мере необходимости.

## <a name="syntax"></a>Синтаксис

```
pushprinterconnections <-log> <-?>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|> < журнала|Записывает файл журнала отладки на пользователя в% TEMP или записывает журнал отладки на компьютер в%виндир%\темп.|
|<-? >|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

Эта служебная программа предназначена для использования при запуске компьютера или в сценариях входа пользователя в систему и не должна запускаться из командной строки.

## <a name="additional-references"></a>Дополнительные материалы

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Развертывание принтеров с помощью групповая политика](https://go.microsoft.com/fwlink/?LinkId=230627)