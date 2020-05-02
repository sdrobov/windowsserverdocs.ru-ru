---
title: pushprinterconnections
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c30afb97-b149-478f-a4b9-2cbc25361818 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 94ba2d09a3e67248a393350e46e971aa8b24b00d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722756"
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

## <a name="additional-references"></a>Дополнительные ссылки

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Развертывание принтеров с помощью групповая политика](https://go.microsoft.com/fwlink/?LinkId=230627)