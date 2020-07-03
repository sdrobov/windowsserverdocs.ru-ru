---
title: pushprinterconnections
description: Справочная статья по команде PushPrinterConnections, которая считывает развернутые параметры подключения принтера из групповая политика и развертывает и удаляет подключения принтеров по мере необходимости.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c30afb97-b149-478f-a4b9-2cbc25361818
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7b22fd5143a9477b40a515df44c9a0b5663dfd7a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931379"
---
# <a name="pushprinterconnections"></a>pushprinterconnections

Считывает развернутые параметры подключения принтера из групповая политика и развертывает и удаляет подключения принтеров по мере необходимости.

> [!IMPORTANT]
> Эта служебная программа предназначена для использования при запуске компьютера или в сценариях входа пользователя, и не должна запускаться из командной строки.

## <a name="syntax"></a>Синтаксис

```
pushprinterconnections <-log> <-?>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
|--|--|
| > < журнала | Записывает файл журнала отладки на пользователя в *% TEMP*или записывает журнал отладки на компьютер в *%виндир%\темп*. |
| <-? > | Отображает справку в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Справочник по командам системы печати](print-command-reference.md)

- [Развертывание принтеров с помощью групповая политика](https://go.microsoft.com/fwlink/?LinkId=230627)
