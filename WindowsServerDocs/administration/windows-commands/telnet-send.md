---
title: telnet send
description: Справочная статья по Telnet Send, которая отправляет команды Telnet на сервер Telnet.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c217abc-1182-466e-914c-1ff16755021b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 44a0415a3516fcb15cd292c9e4c9c0a4a18e5ad9
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85937372"
---
# <a name="telnet-send"></a>Telnet: send

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отправляет команды Telnet на сервер Telnet.

## <a name="syntax"></a>Синтаксис
```
sen[d] {ao | ayt | brk | esc | ip | synch | <string>} [?]
```
#### <a name="parameters"></a>Параметры

| Параметр |                     Описание                      |
|-----------|------------------------------------------------------|
|    AO     |       Отправляет выходные данные команды Telnet Abort.        |
|    айт    |       Отправляет команду Telnet.       |
|    брк    |            Отправляет команду Telnet БРК.            |
|    ESC    |      Отправляет текущий escape-символ Telnet.      |
|    см     |     Отправляет процесс прерывания команды Telnet.     |
|   Синхронизация   |           Отправка команды Telnet Synch.           |
| <string>  | Отправляет любую строку, введенную на сервер Telnet. |
|     ?     |     Отображает справку, связанную с этой командой.      |

## <a name="examples"></a>Примеры
Отправьте их на сервер Telnet.
```
sen ayt
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
